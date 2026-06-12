---
title: "Zotac MAG frontend finally resumes from suspend"
date: 2011-06-12
forum: Mythbuntu
---

### Post by ktmom on 2011-06-12
I experienced the a problem resuming from suspend on my HD-ND01 acting as a mythbuntu frontend. When I put the box into suspend, then try to bring it back out, the IR receiver lights a solid red light, instead of the pulse I normally see when sending commands to it via the USB remote.

This post documents how I finally got it to work.

In the bios I have suspend set to auto. I am not reposting the video on wake. After booting into the OS, you need to make sure that cat /proc/acpi/wakeup shows your USB port enabled for wakeup. If not, search the Ubuntu forms (or mythbuntu or whatever flavor *nix) there are plenty of discussions on how to ensure the proper port(s) are enabled on boot.

Then you need to make sure sudo gedit /etc/default/acpi-support is configured as follows:
ACPI_SLEEP=true
ACPI_HIBERNATE=true
SAVE_VBE_STATE=false
POST_VIDEO=false
I found this [here]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro")

You may need to add "usbcore.autosuspend=-1" to the grub linux command line (again, check the *buntu forums for the proper grub syntax for your OS release). This stops the immediate resume on sleep problem that some have. 

I started using the community help pages: [mythtv power saving]("https://help.ubuntu.com/community/MythTV/PowerSaving") wanting my frontend to suspend and resume via remote.  Following various wake-on-LAN pages and usb remote power pages, the things I changed were:

Copied /usr/share/mythtv/themes/defaultmenu/mainmenu.xml to ~/.mythtv/mainmenu.xml and added the <button> </button> lines there.

In /usr/lib/pm-utils/sleep.d/01mythtv:
```
sudo -u mythtvuser mythfrontend &
```
instead of:
```
sudo -H -u mythtvuser sh -c 'DISPLAY=:0.0 /usr/share/mythtv/mythtv-resume'
```

To make the frontend to wake the backend after coming out of suspend - added to /usr/share/mythtv/mythfrontend (requires wakeonlan installed) :
```
# IP address of backend
SERVER_IP=xx.xx.xx.xx (add your actual BE IP address)
SERVER_MAC=xx:xx:xx:xx:xx:xx (add your actual BE MAC address)
# Send additional wakeup packet here to cover the rare case that backend 
# was shutting down when first one sent
/usr/bin/wakeonlan $SERVER_MAC > /dev/null 2>&1 ;
#
# Use mythTV status port as backend connectivity test
until [ -n "`telnet $SERVER_IP 6544 |grep -i connected`" ]; do
  sleep 3
done
```

---

