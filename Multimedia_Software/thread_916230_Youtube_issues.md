---
title: "Youtube issues"
date: 2008-09-10
forum: Multimedia Software
---

### Post by reazonozaer on 2008-09-10
Hello I am a Linux Newbie and I am actually loving it. I'm running Xubuntu through Wubi. Everything seems to be working fine other than flash, especially youtube videos. They are really choppy. The sound comes though just fine. It is just the video. I don't know how to check my computer in here, but here are the stats as I remember them.

CPU Celeron 1.7 ghz I believe
Graphics Intel 82815 with 4 MG ram
I have 10gb HD for Xubuntu in Wubi
I'm using one of the non shockwave flash plugins.

---

### Post by ad_267 on 2008-09-10
How did you isntall the flash plugin?

There is a new beta 10 plugin from adobe out that might help.

---

### Post by reazonozaer on 2008-09-10
I installed one of the other flash players not the "offical" one. I forget which one it was because there are two options and this one shows up in firefox as macromedia flash player lol. I think it was the one that is not gnash. I really didn't know what the difference was between the three except that one was the "offical" one.

---

### Post by ad_267 on 2008-09-10
Try going to System - Administration - Synaptic Package Manager and search for flashplugin-nonfree and install that.

---

### Post by reazonozaer on 2008-09-11
Thanks for getting back to me. I installed the nonfree flash plugin and it doesn't appear to be any better.

Update: I have also noticed that flash does not seem to be working at all on some sites. I decided to test video playback on MySpace and they didn't even display there. Also a flash audio player wouldn't work either.

---

### Post by rgb1701 on 2008-09-11
> **reazonozaer said:**
> Thanks for getting back to me. I installed the nonfree flash plugin and it doesn't appear to be any better.

Update: I have also noticed that flash does not seem to be working at all on some sites. I decided to test video playback on MySpace and they didn't even display there. Also a flash audio player wouldn't work either.

You shouldn't use anything but the official Adobe Flash plugin at this time- the FOSS alternatives (Gnash et al) aren't ready for prime time yet, though I wish they could be drop in substittutes as soon as possible.

You need to remove the non-Adobe plugin(s) first, then install the Adobe nonfree one from Synaptic.

An easier solution is to simply use Linux Mint 5.0r1 from linuxmint.com.  Mint is Ubuntu with all the media/codec stuff and extras like Java and Adobe Flash already installed for you.

Your Celeron is more than fast enough for Mint/Gnome.

Another issue could be your GPU- 4MB of video RAM is very low by any current standard- I wouldn't use anything less than 16MB for a current web-capable computer.

Also, you need to ensure you have accelerated Intel drivers installed, and not just basic VESA drivers.  Check Synaptic or Intel's site, though the driver issue won't help your video RAM issue.  You might be able to increase video RAM in your BIOs, though I think a better solution would be to get a more recent vintage ATI or Nvidia card with at least 128MB video RAM on board, like

[http://www.geeks.com/details.asp?invtid=VMX400-128A&cat=VCD](http://www.geeks.com/details.asp?invtid=VMX400-128A&cat=VCD)

[http://www.geeks.com/details.asp?invtid=V5500-256A&cat=VCD](http://www.geeks.com/details.asp?invtid=V5500-256A&cat=VCD)

[http://www.geeks.com/details.asp?invtid=V5200-P128&cat=VCD](http://www.geeks.com/details.asp?invtid=V5200-P128&cat=VCD)

[http://www.geeks.com/details.asp?invtid=SFPC44DH128-PB&cat=VCD](http://www.geeks.com/details.asp?invtid=SFPC44DH128-PB&cat=VCD)

---

### Post by reazonozaer on 2008-09-11
> **rgb1701 said:**
> You shouldn't use anything but the official Adobe Flash plugin at this time- the FOSS alternatives (Gnash et al) aren't ready for prime time yet, though I wish they could be drop in substittutes as soon as possible.

You need to remove the non-Adobe plugin(s) first, then install the Adobe nonfree one from Synaptic.

An easier solution is to simply use Linux Mint 5.0r1 from linuxmint.com.  Mint is Ubuntu with all the media/codec stuff and extras like Java and Adobe Flash already installed for you.

Your Celeron is more than fast enough for Mint/Gnome.

Another issue could be your GPU- 4MB of video RAM is very low by any current standard- I wouldn't use anything less than 16MB for a current web-capable computer.

Also, you need to ensure you have accelerated Intel drivers installed, and not just basic VESA drivers.  Check Synaptic or Intel's site, though the driver issue won't help your video RAM issue.  You might be able to increase video RAM in your BIOs, though I think a better solution would be to get a more recent vintage ATI or Nvidia card with at least 128MB video RAM on board, like

[http://www.geeks.com/details.asp?invtid=VMX400-128A&cat=VCD](http://www.geeks.com/details.asp?invtid=VMX400-128A&cat=VCD)

[http://www.geeks.com/details.asp?invtid=V5500-256A&cat=VCD](http://www.geeks.com/details.asp?invtid=V5500-256A&cat=VCD)

[http://www.geeks.com/details.asp?invtid=V5200-P128&cat=VCD](http://www.geeks.com/details.asp?invtid=V5200-P128&cat=VCD)

[http://www.geeks.com/details.asp?invtid=SFPC44DH128-PB&cat=VCD](http://www.geeks.com/details.asp?invtid=SFPC44DH128-PB&cat=VCD)

Thank you for this. Uninstalling the other flash plugin was exactly what I needed to do. Flash works just as good as it did in XP. 

I know the video card in here is old as crap, but it isn't my computer. That is also why I am using Wubi rather than a normal install. It is also why I am using Xubuntu, the video ram and the regular ram are both low on this system, but it is still much faster than XP was, especially on boot up. Now that I have everything everyone else uses working I might be able to talk them into making the switch lol. I know I will be using Ubuntu on my actual computer once we get the wireless card for it. Thanks again for your help.

---

