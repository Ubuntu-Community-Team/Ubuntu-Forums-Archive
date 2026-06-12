---
title: "skype full screen?"
date: 2008-07-14
forum: Multimedia Software
---

### Post by petronell on 2008-07-14
Hi,

I have skype running fine in Hardy.

When I am on a video call and I select the option to put the video call in full screen. It puts the call into full screen but the video image does not resize to full screen.

Rather it stays the same size as the original window and the full screen is a very big black border all around it.

Has anyone come across this? Is there a way to get around this?

Thanks,

daver :confused:

---

### Post by Medieval Cow on 2008-07-15
I had a similar problem. Skype would get all screwy for me when I tried to go full-screen, I'd lose my feed of my own video, and buttons would disappear. Plus my system tray icon would get all screwy. Anyway, I solved it by going into Synaptic, doing a search for Skype, and then uninstalling it, and installing the "Skype-static" package. Don't worry, all your settings will carry over. Dunno if it's the same thing that's causing your problems, but it's worth a try.

---

### Post by petronell on 2008-07-15
Thanks but that package is not in synaptic for me.

Are there any particular archives I need to add in?

daver

---

### Post by tomtarantino on 2008-07-18
I installed the skype static from the medibuntu index:

[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

I am running Skype-static 32bit on a custom built AMD 64 with Hardy.

This did clear up problems with the controls being lost, and the program seems to run and look much better than the standard file.  However, the video still won't resize to full screen.  

I work for a non profit veteran's group and we sue this to VC our staff meetings with our NYC office.  I built the Linux machine because Ubuntu works and we didn't have to shell out a bundle for a VC system. 

If anyone knows how to fix this, it would really help.  I'm afraid I'm a bit of a noob and not very good at diagnostics.

---

### Post by petronell on 2008-07-20
I posted the same question on the Skype forums.

The answer I got back was in the release notes of the latest version of Skype for Linux.

"Non-accelerated X11 output currently doesn't scale video output. This means that in full-screen, the video will be smaller than the available screen size. And similarly, in video preview, you will only see a cropped section of the actual video window."

Looks like the resizing of video that I see on my works WinXP laptop is not supported on linux just yet. :(

Lets hope it gets implemented soon.

daveR

---

### Post by jkyamog on 2008-07-25
I had similar problem with an Acer Aspire 4315 using intel gm965 video.  I saw this thread thinking that it wasn't solved yet.  However after upgrading the latest Hardy kernel 2.6.24.19.21 this has resolved my issue.  Hopefully this resolves yours, especially for the one using skype for a veteran's group.

---

### Post by UdanTU on 2009-04-07
I was able to get around this issue by disabling desktop effects whenever I use Skype. It's a little annoying, but effective for the time being.

---

