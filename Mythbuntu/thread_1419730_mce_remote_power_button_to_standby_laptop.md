---
title: "mce remote power button to standby laptop"
date: 2010-03-02
forum: Mythbuntu
---

### Post by My Name on 2010-03-02
Hi,
i am using a laptop as a remote frontend in the bedroom. I would like to be able to use the remotes power button to put the laptop in suspend, or anything really that will turn the connected monitor off so I can get some kip. Obviously i would like to be able to press the button again and have it wake up.
Is there a simple way to do this? I have had a dig around and found some very complicated methods.

---

### Post by azmyth on 2010-03-02
You can use irexec to tie a button to either a command or a script to execute a command. I prefer to tie it to a shell script as it's easier to edit the script instead of the lircrc file. You can execute a command like xset -dpms off to turn the screen off and change off to on for the opposite. This worked for my computer screen but when I went to a TV this command still left the backlight on so I had to use a RS232 to turn the tv off. You may have to fool around with xset to get it right.

---

### Post by rodercot on 2010-03-02
> **My Name said:**
> Hi,
i am using a laptop as a remote frontend in the bedroom. I would like to be able to use the remotes power button to put the laptop in suspend, or anything really that will turn the connected monitor off so I can get some kip. Obviously i would like to be able to press the button again and have it wake up.
Is there a simple way to do this? I have had a dig around and found some very complicated methods.

 You need to check and mae sure your usb ports are awake so you can resume with the power button. 

 so you need to drop to root.

 **sudo su**

 **cat /proc/acpi/wakeup **

 check and see if your usb 0 is enabled or disabled. 

 if it is disabled then you can do this.

 **echo USB0 > /proc/acpi/wakeup**

 Then issue the 
 
 **cat /proc/acpi/wakeup** 
 
 and you USB0 should now be enabled. if it is than you can add that line to your /etc/rc.local file to get it to stick upon reboot. When you edit rc.local make sure that you stick the line above the exit 0 line and also make sure there is only one exit 0 line in the file. 

 With this complete you can test it fron the command line by issuing a 

 **sudo pm-suspend** 
 
 and the pc will go to sleep. Once asleep you can hit the power button and it should wake it up, if you have ANY problems here than check your /var/log/pm-suspend.log and see what's up. If this all works you can continue.

 now you need to edit your sudoers file to allow pm-suspend to run without a password.

 So still in **root** mode type

 **visudo**

 scroll to the bottom of the file and enter

** "user" ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend **

 The "user" being whatever name you login with. 
 
 now hit ctl-x and then type Y and enter to save the file. Now you can reboot the system.
 
 Once rebooted you can setup the power button via .mythtv/lircrc using irexec and calling pm-suspend for config or to call a script if you prefer. 

 The ideal method is to setup a suspend link in mythfrontend that you need to call via a button action and that way you can never suspend the system with Live TV running which is a no-no.
 
 hope this helps.

 rgds,

 Dave

---

