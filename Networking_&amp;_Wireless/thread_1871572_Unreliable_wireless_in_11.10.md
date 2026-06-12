---
title: "Unreliable wireless in 11.10"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by chrismyers on 2011-10-29
Hi guys,

I am encountering unreliable wireless in Ubuntu 11.10 from various laptops using various wireless cards.

What happens (intermittent problem):

I log-in OK after booting. The wireless attempts to connect, fails & requests the password.[INDENT]Typing in the correct password does not work.

[/INDENT]A reboot cures this problem. I know that there must be a bug, but I am unsure where the bug lies - whether it is in the wireless software (network-manager?) or whether it is in PAM.

Does anyone know of a fix? Or failing that, how can I trace the problem?

Many thanks

---

### Post by rokytnji on 2011-10-29
> Or failing that, how can I trace the problem?

[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

Follow steps 1 through 4 to submit a report and they will get back with you. Good luck.

Edit. Just another route you can take also.

Go the section 4

> 4. Collect information about the bug

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by chrismyers on 2011-10-29
Many thanks.

I have created a new question in Launchpad here:
[URL="https://answers.launchpad.net/ubuntu/+question/176758"]
https://answers.launchpad.net/ubuntu/+question/176758[/URL]

---

### Post by varunendra on 2011-10-30
Hi Chris!

Saw your launchpad question. I think it is same as this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250)

Accordingly, a this may work as a temporary workaround until it is fixed: [http://ubuntuforums.org/showpost.php?p=11360822&postcount=6](http://ubuntuforums.org/showpost.php?p=11360822&postcount=6)

Change *iwlagn* with *iwl4965* in the above post.

---

### Post by chrismyers on 2011-10-30
Thanks for your reply [varunendra]("http://ubuntuforums.org/member.php?u=1043629").

After booting up today, I encountered the non-connect problem.

Running the following two commands suddenly made a connection:[INDENT] sudo rmmod iwl4965

sudo modprobe iwl4965 11n_disable=1
[/INDENT]I am having difficulty in making this permanent as I am unsure where to place the following line:[INDENT] options iwl4965 11n_disable=1
[/INDENT]The following file does not exist in 11.10:[INDENT]/etc/modprobe.d/options.conf
[/INDENT]The files in this directory are:

alsa-base.conf
blacklist-modem.conf
blacklist-ath_pci.conf
blacklist-oss.conf
blacklist.conf
blacklist-rare-network.conf
blacklist-cups-usblp.conf
blacklist-watchdog.conf
blacklist-firewire.conf
nvidia-graphics-drivers.conf
blacklist-framebuffer.conf

Do anyone have any ideas?

Many thanks,

Chris.

---

### Post by chrismyers on 2011-10-30
Regarding the post above. I just created the file & added the line.

I'm unsure whether this has any effect as I don't know whether this option is now switched off.

I suppose time will tell....

---

### Post by varunendra on 2011-10-30
Hi chrismyers,
Yeah, you had to create "options.conf" file to add that line in it. To confirm whether it is effective or not, use *iwconfig*. As opposed to the earlier output (in your launchpad question) > wlan0     IEEE 802.11**abg[COLOR=Red]n[/COLOR]**  ESSID:"SecureMonitored"
 it should now be > wlan0     IEEE 802.11**abg**  ESSID:"SecureMonitored"


If it is, it means the options.conf file is effective now. Hope it improves performance.

---

### Post by chrismyers on 2011-10-30
Thanks again [varunendra]("http://ubuntuforums.org/member.php?u=1043629")

I can confirm that "n" has been disabled.

As the connection problem is intermittent, I can only be sure that this is a fix after about two weeks.

I will update the post with the results - Please someone remind me if I become distracted & forget!

Thanks again.

---

### Post by siddi on 2011-10-30
Hey guys.

Whats the final verdict guys? I recently upgraded to 11.10 too and have the same issues. the wifi keeps dropping and reconnecting

what should i do?

---

### Post by chrismyers on 2011-11-10
I have waited a few weeks to post due to the intermittant nature of the problem.
 
Allthough the problem is nowhere near what it was, it has happened at least once.
 
I wouldn't want to change the thread to resolved, but it is far better.
 
Cheers.
 
P.S. When this did happen. rather than rebooting I just ran the following two commands after ctrl-alt-t:
 
sudo rmmod iwl4965

sudo modprobe iwl4965 11n_disable=1

---

### Post by siddi on 2011-11-13
It says iwl4965 does not exist in proc modules....

the second command returned the starting prompt.... not sure if it is working!!!

---

### Post by chrismyers on 2011-11-13
You are probably using a different driver to iwl4965.

Run this to see:

```
sudo hwinfo --netcard | grep Driver:
```

Modify the command you used earlier to fit your system.

---

### Post by siddi on 2011-11-13
It says hwinfo command not found!!

---

### Post by chrismyers on 2011-11-13
Ah... Try:
[FONT=monospace]
[/FONT]sudo apt-get install hwinfo

---

### Post by siddi on 2011-11-13
Right... i have installed and ran the previous command u gave me and this was returned..

 Driver: "sky2"
  Driver Modules: "sky2"
  Driver Info #0:
    Driver Status: sky2 is active
    Driver Activation Cmd: "modprobe sky2"
  Driver: "iwl3945"
  Driver Modules: "iwl3945"
  Driver Info #0:
    Driver Status: iwl3945 is active
    Driver Activation Cmd: "modprobe iwl3945"

---

### Post by chrismyers on 2011-11-14
Right... You can look at the original commands & use iwl3945  instead of iwl4965.

Cheers.

---

### Post by siddi on 2011-11-14
I tried it... The first time after the second command it said that iwl did not exist.. and the wifi completely dropped and didn't come back.

i rebooted and it came on... and it tried only the second command and it just got back to the original prompt and the wifi is still dropping

:(

---

### Post by siddi on 2011-11-20
It seems to get worse... Now it is dropping every few seconds..

---

