## disclaimeri
this patch was originally posted here: https://github.com/thor2002ro/asus_zenbook_ux3402za/
patch for AMD/I2C interfaced chip was posted here: https://gist.github.com/lamperez/862763881c0e1c812392b5574727f6ff?permalink_comment_id=4727352#gistcomment-4727352 

# asus_zenbook_ux3402za

> You must **disable Secure Boot** from BIOS and fast boot from windows before attempting this fix. Also, Secure Boot must remain disabled afterwards for the sound to continue to work. Shutdown from windows, not restart.

Steps for the sound fix:

* Edit ssdt-csc3551.dsl if needed (optional)

* Build it

```iasl -tc ssdt-csc3551.dsl```

* Copy it in /boot

```sudo cp -f ssdt-csc3551.aml /boot```

* Copy grub script

```sudo cp -f 01_acpi /etc/grub.d```

```sudo chmod +x /etc/grub.d/01_acpi```

* Update grub config
  * Debian / Ubuntu based distributions

    ```sudo update-grub```

  * Fedora / RHEL-based distributions

    ```sudo grub2-mkconfig -o /etc/grub2.cfg```

    ```sudo grub2-mkconfig -o /etc/grub2-efi.cfg```

  * Arch based distributions

    ```grub-mkconfig -o /boot/grub/grub.cfg```

* reboot
