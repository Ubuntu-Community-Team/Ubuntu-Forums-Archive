---
title: "Network Manager"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by evans62 on 2011-01-02
I absolutely cannot get WICD and Network Manager to stop conflicting with each other.  I have followed all the detailed posts on how to completely remove Network manager and WICD still doesn't work.  

After a few days of wasting HOURS on this, tonight I decided to go the other way - remove everything WICD and go with the Network Manager.  
Network Manager Secrets keeps asking me for the password, which is obviously right since it works for all my Windows computers in the house.

When I was trying to use WICD, it would always give me the "Bad Password" spiel.

Will someone PLEASE help me with this before I give up on Ubuntu / Kubuntu for good?  (Yes, I am a Kubuntu guy coming here for help).

:mad:

---

### Post by PatchesTheCaveman on 2011-01-03
It sounds like something else is going that doesn't necessarily involve wicd or NetworkManager.  Did it work before you installed wicd?

And this forum is for all flavors of Ubuntu.  :-)

---

### Post by perspectoff on 2011-01-03
What kind of router and connection key are you using?

Some old routers only allow hex WEP keys, not passphrases. The "Bad password" might be from this.

Might not have anything to do with your choice of Wicd vs. NM.

BTW, removing network manager in Kubuntu requires a few extra steps, like removing network-manager-kde and agreeing to remove the framework when prompted. You also have to reboot once before installing Wicd, or NM doesn't get completely removed.

---

### Post by evans62 on 2011-01-03
Everything worked before the kernel update.  That is what happens, every 2nd or 3rd kernel update breaks my wireless and then I go through it all over again, and every time the fix is a little bit different.

OK, maybe my problem was that I didn't reboot once before installing WICD.  But what about my current configuration, if some part of WICD is remaining and conflicting with NM, how do you completely get rid of WICD?

---

### Post by PatchesTheCaveman on 2011-01-03
You might have been bit by a bad kernel update.  Run this command on a terminal:
```
uname -r
```

If it says *2.6.35-24-generic*, you have the faulty update.  I reported a bug on Launchpad days ago and they finally got around to confirming it yesterday, so hopefully they'll take some action soon.  It's getting really irritating.

At any rate, to work around it, reboot.  If you do not dual boot with Windows or another operating system, hold down TAB before Ubuntu starts to get the GRUB menu.  If you dual boot you always get the GRUB menu.  Choose a kernel earlier than the broken one from that menu.

Your wireless should return to normal operation.  To remove the bad kernel so you don't have to go through this process every time you start your computer, run these commands on a terminal:
```
sudo apt-get remove linux-image-2.6.35-24-generic
sudo apt-get --reinstall install linux-image-2.6.35-23-generic
```

If you want, you can contribute your experience to the bug report so they know exactly how many people this affects and what specific hardware:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)

---

### Post by evans62 on 2011-01-03
Yes, I think that's the one I have - I'll confirm when I get home.  But I was too quick and already deleted the old one, so that's all I have.  

But thanks for letting me know!  It's been driving me nuts.

I guess I could keep using eth0 until the next kernel comes out and then do another update...?

---

### Post by PatchesTheCaveman on 2011-01-03
Since you have a working wired connection, you can install the working kernel by running this command:
```
sudo apt-get --reinstall install linux-image-2.6.35-23-generic
```

And then follow the instructions in my last post to boot into the working kernel and remove the old one.

---

### Post by evans62 on 2011-01-03
I got rid of the suspected kernel and still having problems.  I totally uninstalled WICD, Network Manager, and then did a fresh install of WICD.  For some reason I had to keep adding pieces of it such as WICD-CLI, etc.

Now when I start up I get 

"Password - WICD needs to access your network cards" 

and it never gets started up.

I see a few posts on this "new" problem but can you point me to the specific fix for it?

I am really getting FRUSTRATED over this - I've spent HOURS on this.  I never had this much trouble with Windows.

[SIZE=7]HELP![/SIZE]

---

