---
title: "share / network ubuntu and mac"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2009-02-08
Hello,

I have just set up Ubuntu Hardy off a disk I had lying around on a machine that was running Windows XP and giving me the BSOD. I have almost everything setup such as dvd playback etc. But I need help with networking to my MACBOOK.

1. I can connect to ubuntu shares by going to finder's GO menu and choosing CONNECT TO SERVER. I enter user name and pass and the share mounts on OS X. But I can't see UBUNTU SHARE by browsing in the finder. Why?

2. Same the other way round. Can't browse to shares from ubuntu but can connect by connect to server

3. Mac has built in VNC server and viewer that I used in conjunction with Ultra VNC on Windows. How can I setup VNC between Mac and Linux?

4. Banshee and Rythembox will not connect to my iTunes 8 music share. Is it possible to share music from iTunes to another app in Ubuntu?

that is all i can think of right now. any help would be appreciated. thanks.

---

### Post by darthpenguin on 2009-02-08
Update, I can now see the ubuntu share from finder on the mac. I didn't change or even restart anything it just showed up. weird eh?

still need answers to my other questions.

---

### Post by punx45 on 2009-02-09
i think the ubuntu GUI has enable screen sharing or something to that effect in the menus somewhere.. otheriwse you can install tightVNC.  

by itunes share, do you mean the library sharing that is enabled by itunes?   im not sure what protocol this works on, but it might not be compatible with the other programs.   is your itunes library on the mac?   the easiest thing to do would be to share the itunes folder off the mac to the ubuntu machine and play the music that way.

you should be able to enable sharing on the macbook by going to system preferences>sharing then check off file sharing, then click options and check off "share files using SMB"   i dont know why NFS is not an option.

---

### Post by darthpenguin on 2009-02-09
I am using the itunes library share on the Mac. I used it often with itunes on Windows, I could share the folder I suppose. Could I get banshe or rythymbox or something to watch the shared folder so the library updates when I connect to the share folder?

---

### Post by darthpenguin on 2009-02-10
OK so now I can VNC to Ubuntu from Mac. I can connect to Ubuntu from Mac via Finder. I cannot VNC to Mac from Ubuntu. Buy going to Places --> Connect to server I can connect to Mac file shares but browsing in nutalis or typing smb://192.168.2.13 (mac address) I see "no items" I do not get a password prompt.

any ideas?

---

### Post by punx45 on 2009-02-11
sorry, cant really help you with samba, i have never used it.   but there are plenty of good tutorials on how to set it up.

---

### Post by issih on 2009-02-11
itunes sharing from mac to ubuntu won't work as the later versions of daap (the protocol itunes uses) contain encryption that apple keeps to itself. ubuntu to mac works pretty well (just enable the plugin in rhythmbox or install something like mediatomb).

In essence linux daap sharing uses an earlier version of the protocol that has been cracked, but because itunes has backwards compatability these shares still show up on the apple.

One potential work around is to use tangerine:

[http://snorp.net/tangerine/](http://snorp.net/tangerine/)

to share your itunes library from the mac, as that still uses an older version of daap and the shares are seen by rhythmbox.

Hope that helps

---

### Post by darthpenguin on 2009-02-11
Hey thanks, I might try Tangerine. I do miss sharing my library but it is not that important anyway. Too bad apple felt they needed to typescript daap.

also I can connect to Mac by typing smb://192.168.2.13/sharename in nautilus. It must just be a but with browsing. Hope they fix it soon.

---

### Post by FishRCynic on 2009-02-11
do you share in ubuntu via /etc/samba/smb.conf or with gui (gnome) shares?

if you don't gui share ...

out of curiousity if you were to enable a gui share (right click in nautilus and share of folder) and restart samba does your nautilus suddenly see the other computers?

(i have wins set up - and would have to disable it or i would test this myself)

---

### Post by Goatrancer on 2010-02-08
Yeah I am having similar problems. I successfully set up sharing from ubuntu to mac by following various instructions, some stuff through the GUI and some stuff through the terminal editing the samba.conf file
Nothing I do will allow me to see my SMB shared folders from my mac though.

Navigating to my mac via network in the GUI does not prompt me for a user/pass and gives me an error. (Unable to mount location. Failed to retrieve share list from server)
If I type smb://my macs IP address the same thing happens. I've tried various stuff described in these forums via the terminal and not matter what the problem is essentially the same: Ubuntu can see my mac but not get anything from it or get a user/pass prompt.

I'm a linux/command line novice so if the info I've given is confused and unhelpful, my apologies, I am confused!!

---

### Post by bkadoctaj on 2010-02-23
> **Goatrancer said:**
> Yeah I am having similar problems. I successfully set up sharing from ubuntu to mac by following various instructions, some stuff through the GUI and some stuff through the terminal editing the samba.conf file
Nothing I do will allow me to see my SMB shared folders from my mac though.

Navigating to my mac via network in the GUI does not prompt me for a user/pass and gives me an error. (Unable to mount location. Failed to retrieve share list from server)
If I type smb://my macs IP address the same thing happens. I've tried various stuff described in these forums via the terminal and not matter what the problem is essentially the same: Ubuntu can see my mac but not get anything from it or get a user/pass prompt.

I'm a linux/command line novice so if the info I've given is confused and unhelpful, my apologies, I am confused!!

I'm in the same exact place.  :(

---

