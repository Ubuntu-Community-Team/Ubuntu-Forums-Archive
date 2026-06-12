---
title: "[SOLVED] I get no sound with my usb sound card in Firefox 3 beta 5"
date: 2008-05-20
forum: Multimedia Software
---

### Post by djdarrin91 on 2008-05-20
I get no sound through my usb sound card in Firefox 3 beta 5(Ubuntu 8.04). it works fine in movie player etc.. Just no sound on FF :confused:Anyone know how to fix this? Thanks in advance for any help:) by the way there is no name brand that i can see on the card,but on top it says:3D Sound and the bottom has a sticker that says: Model KY-360 USB 3D Sound. hope that may help.

---

### Post by djdarrin91 on 2008-05-20
I just solved the problem.(This worked for FF3 beta 5 and Amarok for me)

I had to comment the line related to the snd-usb-audio option in the /etc/modprobe.d/alsa-base file from :

options snd-usb-audio index=-2
to:
#options snd-usb-audio index=-2
...

Now the sound works under FF3 beta 5 and Amarok.
(Just sudo gedit /etc/modprobe.d/alsa-base  make the change and save.)

---

### Post by Penguin-Guru on 2009-08-18
I've been having the same problem and this solution is the only one I've found so far but I'm new with linux so I'm having problems. I sudo gedit /etc/modprobe.d/alsa-base and the file is empty. There is nothing to change. I close it and it asks if I want to save changes so I say no. I'm probably just missing something but if anybody knows what I should be doing please let me know.

Email: [email]Penguin-Guru@heathgroup.net[/email]
Skype: Penguin-Guru

---

### Post by aaronchall on 2009-09-19
This guy's fix is probably out of date, because he wrote it back in May of 08, WAY before Jaunty Jackalope.

Yeah, I ordered one of these from overseas (hongkong, I think) and the branding on the box says Comodow. The model number on the USB doohicky says HY 554.  

I got it to work with the audio player on a CD, but it doesn't work for web pages or Skype.  

I downloaded a driver from Comodow's site, it's in .rar format, so I'll need an unpackager, anyone have suggestions?  (Yeah, I'll look through the rest of the forums, and post back here when I've tried it...)

Aaron

---

### Post by aaronchall on 2009-09-19
The driver is only good for Windows.  Maybe there's a generic usb audio card driver?  

I'll keep looking...

---

### Post by jas007 on 2009-11-16
> I've been having the same problem and this solution is the only one I've found so far but I'm new with linux so I'm having problems. I sudo gedit /etc/modprobe.d/alsa-base and the file is empty. There is nothing to change. I close it and it asks if I want to save changes so I say no. I'm probably just missing something but if anybody knows what I should be doing please let me know.

Email: [email]Penguin-Guru@xxxxxxxxxxx.net[/email]
Skype: Penguin-Guru

Try

```
sudo rm /etc/modprobe.d/alsa-base[\CODE]
if you created the alsa-base file. Edit the required file using (on jaunty)
[CODE]
sudo gedit /etc/modprobe.d/alsa-base.conf

```
as djDarrin said earlier change the line
```
options snd-usb-audio index=-2
```
to 
```
#options snd-usb-audio index=-2
```

Than I had to:
```
asoundconf list
```
to list the avaliable sound cards

Than I set the defualt sound card to 'Headset' in my case using
```
asoundconf set-default-card Headset 
```



hope that helps.

---

