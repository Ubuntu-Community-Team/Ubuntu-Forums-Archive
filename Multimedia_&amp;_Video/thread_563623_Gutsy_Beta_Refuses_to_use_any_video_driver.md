---
title: "Gutsy Beta: Refuses to use any video driver"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by Game_boy on 2007-09-30
EDIT: Fixed myself, see post below. It's still a bug though.

--

I performed a distribution upgrade from a stable, working Feisty to Gutsy Beta. 

The process went fine, but on rebooting I was put on the display configuration screen with just VESA (I was previously using fglrx 8.41 fine) and whatever buttons I press,  it tells me it's going to restart, flickers and then goes back to the config screen with options back to default. One clue may be that the "Location" bar at the top of the screen is blank and glitchy when pressed.

Nothing I do makes it enter GNOME or use fglrx, and there's no way to power off without physically disconnecting it.

System:

Samsung 913N Monitor (LCD, unrecognized as a preset)
ATI Radeon X1950PRO 512MB GPU
Intel Core 2 Duo E6400 CPU
ASUS P5ND2 SE Motherboard

---

### Post by bwallum on 2007-09-30
I can confirm this, just blown up my running Fiesty using the upgrade to Gutsy root.

Having done the download etc and gone for restart the following is as Game_boy's experience.

You are presented with a small app window that has two tabs, Screen and Graphics Card. No matter what you choose, either the defaults or your own specific monitor and card, when you press ok the sytem reverts to a full screen terminal display. It then displays for one second, goes blank for half a second. It repeats this for a total of 3 times. It then returns to the small app window with the Screen and Graphics Card tabs.

If I press esc as Grub boots then I can choose the recovery mode and get a stable full screen terminal. I can see that my work files are ok by using the ls command in the terminal. 

How do I get back to my stable Fiesty please? 

Bob

---

### Post by Game_boy on 2007-09-30
I managed to fix it for me.

I just chose the fglrx driver and then manually disconnected power instead of pressing OK. When I started the computer I chose 2.6.20 kernel (Don't know whether that made a difference) and it was fine from there. It seems to be using the default restricted fglrx driver now instead of 8.41.

---

### Post by bwallum on 2007-09-30
Thanks Game_boy

Your fix worked for me too. I tried the default kernel but it did not work. I used esc as grub booted and choose the earlier version offered. All went well. Then tried to set up for my monitor when at the desktop. This resulted in the desktop being displaced horizontally and vertically although the mouse pointer responded as though the desktop was displayed correctly. Bizarre! Trying to move the mouse pointer to highlight menus and buttons with the pointer displayed some way away was very amusing!

Now on Gutsy, thanks again

Bob

---

### Post by katharos on 2007-10-01
I'm pretty sure that restarting at that particular point does nothing.
I had the same weird looping problem whenever I tried the default kernel from grub, but trying the older (third on the list) option worked fine before i tried the restart-at-this-point thing. It made no change, you were always able to load the old version fine. 

I found a very similar problem in another thread, where a guy had "fixed" it by removing or renaming  the xorg.conf file from /etc/X11/ 

I tried this and it worked for me, I am now able to boot the new kernel and everything except the nvidia drivers is working. The restricted repository still requires the xorg.conf file, but I think the move to gutsy is (eventually) meant to make the xorg.conf file redundant so i'm not sure what's happening there.

I'm not sure if this counts as a fix, but it's worth a shot, just make sure you back-up your xorg.conf

---

### Post by katharos on 2007-10-01
> **Game_boy said:**
> I managed to fix it for me.

I just chose the fglrx driver and then manually disconnected power instead of pressing OK. When I started the computer I chose 2.6.20 kernel (Don't know whether that made a difference) and it was fine from there. It seems to be using the default restricted fglrx driver now instead of 8.41.

Well i think it did make a difference. The re-start does nothing, using the older kernel does. Of course in using the older kernel you're not really changing anything, just kind of bypassing the problem.

---

### Post by valchau on 2007-10-07
HELP!! I am in the same situtation. There I was happy with Feisty and I made a terrible mistake in upgrading last night to Gutsy. At this point I just want to roll back to Feisty. How can I do that? This video problem is driving me NUTS!!! I can hardly do anything now with such large PRINT...

I can't get it to recognize my video drivers as the other writers pointed out. I just can't figure out how to fix this. And the boot up is WEIRD. no longer a user friend LINUX!!! Should I try kubuntu??? (PS this window is doubled as well)...

---

### Post by katharos on 2007-10-07
ok, I've been working on getting my nvidia drivers back up and running but no luck so far. 

I can still use my machine as normal just can do anything which requires lots of graphics processing.

In my searching i discovered that the weird graphics settings panel we seem to be getting stuck on is the bulletproof X system. which is new in gutsy. It's designed to be a troubleshooter. In that if X doesnt start up properly for whatever reason, it gives you the opportunity to change the settings then start up. Unfortunately it doesnt seem to be working correctly for some reason. As in, not matter what changes i make i end up back at the bulletproof X panel.

see: [https://wiki.ubuntu.com/BulletProofX]("https://wiki.ubuntu.com/BulletProofX")
and: [http://arstechnica.com/journals/linux.ars/2007/08/29/ubuntu-xorg-maintainer-demonstrates-bulletproof-x]("http://arstechnica.com/journals/linux.ars/2007/08/29/ubuntu-xorg-maintainer-demonstrates-bulletproof-x")

ooh, i just found this site: [http://people.ubuntu.com/~bryce/BulletProofX/]("http://people.ubuntu.com/~bryce/BulletProofX/"). It goes through what bulletproof X is meant to do and how. It also says that trying generic monitors in the settings doesnt work yet. That's what i was trying before, so i'm going to go back and try some other ones.

I'm currently doing ok in gutsy without a xorg.conf file. If you havnt tried this already, when you get stuck at the bulletproof X panel, press ctrl-alt-F1 to log in to a terminal and go to /etc/X11/ and rename your xorg.conf file to something like xorg.conf.backup and then type shutdown -r now, to reboot.

---

