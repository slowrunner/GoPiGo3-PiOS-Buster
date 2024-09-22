## The supported OS for the GoPiGo3 is the GoPiGo OS (version 3.0.2 29Mar2022)  

- Burn this to your card: https://gopigo.io/downloads/gopigo_os  
- Follow these instructions: https://gopigo.io/gopigo-os-v-3-0-2/  


**But if you want the GoPiGo3 software on 32-bit Pi OS Buster**
**which is no longer called "Pi OS (Legacy)" then follow the instructions below.**

<br>
<br>

# GoPiGo3 Software Install over Archived "Legacy" 32-bit Buster PiOS

Link to archived "Legacy (Buster) 32-bit Pi OS":
```
  https://downloads.raspberrypi.com/raspios_oldstable_armhf/images/raspios_oldstable_armhf-2023-05-03/
```

1) Download 2023-05-03-raspios-buster-armhf.img.xz to your desktop or laptop

2) Download latest Raspberry Pi Imager from https://www.raspberrypi.com/software/

3) Run Raspberry Pi Imager (v1.8.5 used 2024-09-22)
- Select Device:  (cannot be Pi5)
- Select Operating System:
  - Use custom -> navigate to 2023-05-03-raspios-buster-armhf.img.xz -> Open
- Choose Storage
- Edit Settings
  - user: pi  <-- must configure user pi 
  - configure WIFI: (Remember SSID is case sensitive)
  - 

4) Boot the image (does not need to be on a physical GoPiGo3 at this point),  
-  ssh into it or from an attached monitor and keyboard:

5) Update the OS:
```
sudo apt update
sudo apt -y upgrade
sudo reboot
```


6) Install GoPiGo3 API

Execute:
```
curl -kL dexterindustries.com/update_gopigo3 | bash
curl -kL dexterindustries.com/update_sensors | bash
```

7) FIX Broken Python3 Installation of I2C_mutex (Dexter-AutoDetection-and-I2C-mutex egg)
```
cd ~/Dexter/lib/Dexter/RFR_Tools/miscellaneous/
sudo python3 setup.py install
``` 

8) Test your installation:
```
python3
>>> import I2C_mutex
>>> import di_sensors
>>> (ctrl-d)
```

Kudos to [https://github.com/jimharris1993](https://github.com/jharris1993) for [finding this workaround](https://forum.dexterindustries.com/t/reprise-no-module-named-i2c-mutex/9957)
