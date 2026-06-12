---
title: "Video card recomendations please"
date: 2009-10-22
forum: Multimedia Software
---

### Post by royalwithcheese on 2009-10-22
I'm currently using my motherboard's integrated geforce 8200 chipset for video out. I have had persistent issues with the drivers I've found for this chipset and I've decided to upgrade. 

My computer is hooked up to a 40 in HDTV via VGA cable. I've tried using an HDMI connection, but I could never get both the audio and video to work at the same time.

What I'm looking for is a video card with drivers that will work well with 9.04 and will give quality high resolution video on my HDTV. I'm open to using either VGA or HDMI connectivity as long as HDMI audio playback from the video card functions properly.

I humbly request your recommendations as to what video card I should purchase. I don't want anything too high end, just something functional.

---

### Post by cilynx on 2009-10-23
In your position, I would try harder to get the NVIDIA drivers working.  When it comes to quality graphics with any degree of control under Linux, you're only real options are NVIDIA and ATI.  In my experience, ATI is the harder of the two to get to work well.

---

### Post by vinutux on 2009-10-23
Being a ATI user i think Nvidia is better supported under linux...........

---

### Post by tubasoldier on 2009-10-23
I've got both Nvidia and ATI cards. In Linux Nvidia wins.
I've also set up systems with integrated Intel chipsets. When they work they work great.

---

### Post by royalwithcheese on 2009-10-23
is there a card by Nvidia that will have better functioning drivers than the chipset I have currently? when I install the drivers on my geforce 8200 my highest allowable resolution is 768 x 480. is there some source other than Nvidia that I should look at for drivers?

---

### Post by cilynx on 2009-10-23
Something is definitely not right with your configuration.  I used to run a GeForce FX 5200 at 1440x900 and I'm currently running a Quadro NVS 280 driving two displays at 2800x900.  I'm using the non-free module built through module-assistant.  It works great with either Twinview or Xinerama.

---

### Post by royalwithcheese on 2009-10-24
When I installed I stopped GDM and ran

sudo sh /.../NVIDIA-Linux-x86_64-185.18.36-pkg2.run

I told it to compile the kernel itself and then I rebooted when the process finished. The computer started in 620x480 and can't go any higher.

Is there some step I missed? Is there some other way of installing this driver that will work better? or maybe some other driver that I should use instead?

---

### Post by cilynx on 2009-10-24
A couple of things to try:

run 'sudo module-assistant'

Select 'UPDATE' to make sure the background stuff is up to date.

Select 'PREPARE' to make sure your build environment is ready.

Select 'SELECT'
Check the box next to 'nvidia-kernel' then select 'OK'

Select 'GET'.  It will download source packages
Select 'BUILD'.  It will build the module
Select 'Yes' to install the new module

After that, you can exit out of module-assistant.  From here, you can load the new nvidia kernel module and see if it works.  If you're not really up on how modules come together, it may be best to do a reboot.

If that doesn't work, there's a thread about your mobo that may help you out over here:

[http://ubuntuforums.org/showthread.php?t=822315](http://ubuntuforums.org/showthread.php?t=822315)

---

