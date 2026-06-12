---
title: "Myth won't start, &quot;Cannot connect to X server&quot;, Nvidia"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by little_penguin on 2007-07-29
Hi there,

I am struggling with Mythtv and I would really appreciate any help to get it working. When I try to run the program by logging into a Mythtv session in the login manager, all I see is the Mythtv logo and it just hangs there and won't start. If I try to run it from the command line, I get:

# mythtv
mythtv: cannot connect to X server

I tried running sudo dpkg-reconfigure xserver-xorg
but it didn't help.

I have an Nvidia GeForce 7650 GS video card, with the nvidia-glx-new restricted driver from the Ubuntu repositories already installed and configured.

After some research, I think the source of my problem is that my Nvidia graphic driver was already installed *before* I set up Mythtv backend and frontend.

Because, in the Howto at:

[https://.help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://.help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

it says "Proprietary ATI and NVidia video drivers should be installed and configured after MythTV installation and configuration is complete."

Is it easy to correct this? I don't want to botch anything up by doing the wrong thing. Do I literally uninstall the nvidia-glx-new video driver and reinstall it again, or do I need to enter some command or run some setup utility to make my Nvidia work with Mythtv?

Thanks in advance,
Regards,
little_penguin

---

### Post by blcvegas on 2007-07-30
If it's a driver problem, you should be able to disable the Nvidia driver and re-start the program.

To clarify, are you seeing this when you start the frontend application or when you're doing the backend setup?

---

### Post by little_penguin on 2007-07-31
> **blcvegas said:**
> If it's a driver problem, you should be able to disable the Nvidia driver and re-start the program.

To clarify, are you seeing this when you start the frontend application or when you're doing the backend setup?

Hi blcvegas,

Ok I just disabled the Nvidia proprietary driver by putting the open source driver "nv" in my xorg.conf, however the problem remains. Mythtv still won't start.

Are there maybe any log files I could post that might help?

Yes, as far as I know the backend is configured OK, I see the error when I try to start the frontend. I am using the Ubuntu mythtv package and the proprietary nvidia driver was already installed and configured before I installed mythtv.

I'm not sure what the best thing to do is - should I completely uninstall mythtv and nvdia and start from scratch, perhaps I forgot a setting somewhere.

Thanks and regards,
little_penguin

---

### Post by little_penguin on 2007-08-04
Unfortunately, have searched high and low on the web, including the Mythtv forums, followed the Howtos to the letter, but still didn't get this working. I tried completely purging Mythtv as well as the Nvidia driver, and reinstalling. Got the same errors :-(. I reckon it probably needs to be done on a clean install of Ubuntu, would only do that as a last resort. For the time being I am going to give Freevo a try.

---

