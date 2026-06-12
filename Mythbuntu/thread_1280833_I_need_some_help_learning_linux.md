---
title: "I need some help learning linux"
date: 2009-10-02
forum: Mythbuntu
---

### Post by ConXtionS on 2009-10-02
Hi guys

I need to do this......

-------------------------------------------

 				 				**Re: Choppy Live TV** 			
 			 			 		   		 		 		newlinux you are a lifesaver.

I was wondering why the line:

/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext

kept coming up, and I was SURE I had the correct /etc/X11/XvMCConfig file.

However after going through it I noticed that I had originally created a file called XmVCConfig (not XvMCConfig). Pushing the "up" cursor on my terminal for commands for the past two weeks kept me making this mistake. (See my second post for the proof! :razz:)

I have changed it now - and - thankfully - the OSD is B&W, and my 1080i is displaying pretty well! It takes 5-6 seconds for the audio and video to sync up but after that I can't complain! 

Even HD basketball recordings are coming in clear! Anything above 70% signal strength comes in really well. March madness here I come.....

Thanks to all (esp. newlinux) for your help, and if anyone else is looking for a fix to this, here is the directions for my fix (note this only pertains to nvidia users):

1)  Make sure you have the correct driver to display XvMC.  Synaptic or Envy can do this.
2)  Change or create your /etc/X11/XvMCConfig file to display libXvMCNVIDIA_dynamic.so.1 
3)  Change your /etc/x11/xorg.conf file.  Make sure your driver is set to "nvidia" and not "nv".

Also, under device, add the lines:

Option "RenderAccel" "true"
Option "NVAGP" "0"
Option "UseEvents" "True"
Option "XvmcUsesTextures" "false"


Note - some people think putting a "1" or "2" into the NVAGP line works better for them.  

4) Set your playback profiles (as suggested by newlinux) to using standard xvmc decoder and xvmc-blit, 1CPU, bob 2x deinterlacer, and one field fallback deinterlacer.


For more info see 

[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

Everything you could think of will be on there.

Avoid Typos.  It will save time in the end :wink:

-----------------------------------------------------------

My problem is... I have no idea how to get to those files or edit them?

Help please????

thanks

Jim

---

### Post by ConXtionS on 2009-10-02
I moved my post to the noob channel where it probably belonged in the first place
 
sorry bout that guys

---

### Post by sawbuck on 2009-10-03
Where is teh noob channel.  I could use.... seriously.  I see stuff in the various myth logs that has me really banging my head,

---

