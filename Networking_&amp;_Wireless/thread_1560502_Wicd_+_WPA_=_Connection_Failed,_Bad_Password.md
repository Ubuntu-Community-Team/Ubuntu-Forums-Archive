---
title: "Wicd + WPA = Connection Failed, Bad Password?"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Dyno23 on 2010-08-24
Scouting on the internet for this issue.  Wireless card is (finally) working.  I am one of the many getting the "Connection Failed: Bad Password".  

I have tested the password on a different machine to make sure and it does connect.  One of the "fixes" seems to be to roll backwards on Wicd. Wondering if there is any information I am not seeing?

---

### Post by aysiu on 2010-08-24
That fix didn't work for me.

What worked for me was uninstalling *network-manager* and *network-manager-gnome* and then rebooting.

---

### Post by Dyno23 on 2010-08-24
I am a big time newbie here so pardon me if I'm wording this wrong but I was lead to believe that Wicd was a sort of replacement for network-manager.  I've purged network-manager... I think?  All my wireless stuff is going through Wicd right now.

---

### Post by Dyno23 on 2010-08-24
re-read your post...sorry.  network manager is unistalled.  not sure if gnome is on here or not...

---

### Post by Dyno23 on 2010-08-24
gnome is not.  just wicd.

---

### Post by aysiu on 2010-08-24
> **Dyno23 said:**
> re-read your post...sorry.  network manager is unistalled.  not sure if gnome is on here or not...
After you uninstall Network Manager, you still need to reboot.

---

### Post by BkkBonanza on 2010-08-24
Check how the password is entered in Wicd. I have had problems in the past that it required a different format than expected. I seem to recall once with WPA that it had to be encoded. If you look in the /var/lib/wicd/configurations dir and view the cfg file there and the psk line looks different then you entered it then I think it may be an issue like that. I know I had trouble with this but can't recall off hand what the correct format was. You think they would make it simpler.

I like Wicd and prefer it over Network Manager but I did have some problem with this back when I set it up.

Edit: Was just googling. One thing is to try quotes "..." around the key. It may be it expects hex if no quotes. Not sure, but worth trying. I may have had to convert the password to hex when I did it.

---

### Post by Dyno23 on 2010-08-25
Uninstalls happened, rebooted, no dice.  Checked out that config file (cool...and creepy...hey look there's my PW) and it's right on.  Going to bed it took me forever tonight just to get the wired thing going...haha.  I will try quotes then hit the hay and look at this some more tomorrow.

A very common consensus still seems to be downgrading wicd to 1.6.  I have no idea how to do that.  Googling has been fruitless.  I think my query phrasing is wearing down on me as my mind scatters.  IF the quotes thing works I'll post.  If it doesn't I'll talk to you tomorrow :)

---

### Post by BkkBonanza on 2010-08-25
Another file to verify the password actually passed to wpa_supplicant (for WPA handling) is /etc/wicd/wireless-settings.conf.

This is starting to come back to me and I recall having to run wpa_supplicant in debug mode in a terminal to see the messages it dumped out during negotiation. This helped me see exactly what was going wrong. It's a bit crazy though for something that should be easy.

---

### Post by Dyno23 on 2010-08-25
Well the PSK looks like it's an encrypted value...very lllllllong string which does not equal my PW.  I am going to try and figure out how to downgrade to wicd 1.6 I think.  See if that works.

---

### Post by diego73 on 2010-12-05
This is that work for me.
 
 After try the last versions from the original ubuntu repos of network manager and  wicd, change router configuration and  wpa_supplicant without any positive results to connect to my house  wireless, then I decide to update the kernel version of my notebook from  2.6.32.xx to 2.6.35.22 and congratulations that work.

Some Data:
   Distro: Ubuntu 10.04
 Notebook: Sony Vaio VGN-N320E
 Router: Linksys WRT160N V3

Steps to kernel update:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

Some more:
Both WiCd & network manager work perfectly after update.

Before the error I have as police accept all automatically updates from ubuntu, but now I put much attention to the updates before accept it's. The old police take me to much nightmare.

Now I enjoy my wifi :razz:!!!!

---

### Post by nobann on 2012-11-06
Hi,
First message here, I got same error when sometimes the network essid contain special characters such as ' .

---

### Post by wildmanne39 on 2012-11-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

