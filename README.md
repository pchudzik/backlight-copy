# backlight-copy

This script will copy brightness settings from source device to destination device.
 
Copy process is required for me because I have two graphic cards. One is integrated intel and second
is amd radeon. When xfce power manager decides on what device brightness should be set it uses first
available (I think). For me it decides to use intel card which is not used for display.

I haven't found any working solution which will allow to select on destination device in xfce power
manager. To make this work I decided to write simple bash script which will monitor for changes in
intel_backlight (acpi_video1) and copy current brightness level to destination decided. So it will
copy brightness level from intel card to amd card.

# How to install

## requirements
ionotify binary must be installed:
```sudo apt-get install```

## installation
copy backlight-copy to /usr/local/sbin
copy backlight-copy.init.d to /etc/init.d directory and configure this script to be executed on boot.

```bash
sudo cp backlight-copy /usr/local/sbin
sudo cp backlight-copy.init.d /etc/init.d/backlight-copy
sudo update-rc.d backlight-copy defaults
```

and that's all now when you change brightness level using fn keys intel brightness settings will be
copied to radeon card.
