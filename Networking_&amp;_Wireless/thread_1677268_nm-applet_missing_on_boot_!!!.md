---
title: "nm-applet missing on boot !!!"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by Muzafsh on 2011-01-28
Hi,

I have hit upon this strange bug...

When i booted into my Ubuntu 10.10, i found the nm-applet missing as a result no internet connection (both wi-fi as well as mobile broadband and ethernet too)

following done...

1. First I have tried to re-install the following file 'network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_i386.deb" but that didn't fix the missing nm-applet 

2. 'Notification area' visible (bluetooth, volume and keyboard applets showing there but no nm-applet)

3. Added a new entry to 'startup applications' with the command 'nm-applet'. To no avail, on reboot the nm-applet still missing.

4. I clicked on 'network connections' and found that my wireless and mobile broadband profiles i had created and had been using before this issue were intact.

But i am not able to connect from the network connections window or make it appear as an applet in the notification area. Any help is most appreciated.

5. Checked the following in gconf-editor
 Systems->networking->connections ... my connection profiles present there.

6. Opened terminal tried stopping network-manager and restarting with the commands 'sudo stop network-manager' and sudo start network-manager' but no luck with nm-applet.

7. Executed the command 'sudo nm-applet', eureka !!!

The network applet appeared but my profiles were missing.

It seemed like this was a totally new instance of the applet but when restarted the machine, it turned out the fix wasn't permanent.

Issue still looming large, when re-executed the command the applet appeared(a new instance again) at least the consolation was that i could establish connections (both thru my wireless and mobile broadband connections) but only by creating a new profile for both type of connections.

like to add that the terminal continues to stay active with lines of code showing up, However closing it forcibly did not interrupt the nm-applet instance that was started.

8. After doing the above i looked into 'gconf-editor' but could not find the newly created profiles in this new instance of the applet.


Please help me restore my network-manager-applet in my Ubuntu 10.10

Until then i hope to utilize the workaround of 'Point 7' for as long as it works :(

PS: Let me know if you need to look into any of the logs or command outputs (But please be precise with the instructions for troubleshooting/diagnosing my issue as i am not an expert at understanding an experts tech-talk-references)

thanks

---

### Post by grahammechanical on 2011-01-28
I do not have the answer. Please do not think that I do. Consider this:

1) Use Software Centre or Synaptic to uninstall network manager and then re-install it. Reboot in between.

2) Make sure that there is a tick against Network Manger in Startup Applications. Reboot.

Regards.

---

### Post by dineshs on 2011-01-28
Try step-I [here ]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")then reboot
Or 
Run ```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
set [COLOR="DarkRed"]managed=true[/COLOR] and restart

---

### Post by Muzafsh on 2011-01-29
thanks for looking...

**@grahammechanical**
[HTML]1) Use Software Centre or Synaptic to uninstall network manager and then
re-install it. Reboot in between.[/HTML]

Well this attempt is possible for the first half, as once i uninstall the network manager from the synaptic then my internet will be down as a result i can't re-install from the synaptic.

Hence my Point 1. where uninstalling carried out through synaptic and re-installed it through the pre-downloaded file.

**@dineshs**

my file '/etc/network/interfaces' has only the following 2 lines of code
[HTML]auto lo
iface lo inet loopback[/HTML]
so i didn't have to change/edit anything.

[HTML]gksudo gedit /etc/NetworkManager/nm-system-settings.conf[/HTML]

no luck with the flag set to 'True'

**currently surviving on my procedure No. 7**

---

### Post by dineshs on 2011-01-29
> 2. 'Notification area' visible (bluetooth, volume and keyboard applets showing there but no nm-applet)Did you try
Right click on top panel-add to panel-Select notification area-add

---

### Post by Muzafsh on 2011-01-29
Yup, i tried to add another notification area by right clicking on the bottom panel. But the nm-applet did not load with it.

---

### Post by Muzafsh on 2011-02-01
Hi,

Is there nobody who can look into the bug i have reported ???

thanks,

---

### Post by Muzafsh on 2011-02-02
Well i don't know if i have fixed the actual issue or just ended up creating a functional workaround.

After my workaround failed to work anymore, i started researching again for a solution.

I went to System->Preferences->Passwords and Encryption Keys.

1. I deleted the entry 'Login' found in the passwords tab.

2. I then created a shortcut under System->Preferences->Startup Applications with the following

Name : Network Manger Applet
Command : /usr/bin/nm-applet
Comment : Launch at login

saved it and ensured it was 'checked'

**Wallah ! i restart my OS and there the nm-applet was back.**

It seems the keyring password was the cause of the problem i was facing. and resetting it by deleting it, seemed to have fixed the issue.

:)

---

### Post by jrev on 2011-02-04
I am on Ubuntu 9.04 with the same problem and could not find the menu :
Preferences->Passwords and Encryption Keys.

I wonder where to pick it up

I added the application at start up without any success

---

### Post by Muzafsh on 2011-02-05
**@jrev**

did you try running 'sudo nm-applet' in the terminal ?

Please post the outcome

----------------------------------

BTW i am re-opening the thread as the issue has relapsed

This bug needs to be looked into by an expert of this community.
Please find the error when i try to run 'sudo nm-applet' from the terminal

[HTML]
sudo /usr/bin/nm-applet
[sudo] password for muz: 
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area

** Message: <info>  No keyring secrets found for Auto AMyCon/802-11-wireless-security; asking user.

** Message: <info>  No keyring secrets found for Tata Docomo (GPRS)/gsm; asking user.



** ERROR:applet-device-gsm.c:781:gsm_get_secrets: assertion failed: (info)
Aborted

[/HTML]

hope the above error should help in understanding things better.

thanks,

---

### Post by Muzafsh on 2011-02-06
it seems the SIM pin entry to my 3G device is causing the nm-applet error and restricting it to start on boot or from the terminal.

I have a dual boot ubuntu with Win 7, when i try to directly boot into Ubuntu the nm-applet issue prevails. But if i restarted from there into Win 7 and then entered the SIM pin in Win 7 and then restart it from there back into ubuntu the nm-applet shows up in the notification area.

Can an Ubuntu geek help diagnose this issue and offer a fix to it.

If you need any logs please let me know.

thanks,

---

