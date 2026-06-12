---
title: "Skype functional with Gigaware 25-496 webcam"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Andy H. on 2009-11-18
After checking various [forum posts]("http://http://ubuntuforums.org/showthread.php?t=956688&highlight=set+Skype+recognize+webcam") on how to get skype to work with a webcam in Linux,[ homemade drivers]("http://www.kaiser-linux.li/index.php?title=PAC7311"), and the like, I have been able to do it fairly simply and with minimal downloading of extra applications.

**Hardware:**

HP Pavilion ze5400 Laptop (about 6-8 yrs old, my Linux experimental machine)
[Gigaware 25-496 webcam]("http://www.radioshack.com/product/index.jsp?productId=3379767") ($40 at Radio Shack)

This assumes you've downloaded the Skype for Linux and installed it (this was done with beta v. 2.1.0.47)

**Steps:**

Make sure audio input is set.  I'm using Pulseaudio which came preloaded with Ubuntu, I think.   Start from "Applications> Soundand Video >Pulseaudio >input devices tab" and adjust mono slider bar to middle, talk to it and see if the little bar underneath registers the sounds you're making.

Start Skype

Right click on the small green skype indicator in the upper right corner by the date /sound indicators in Gnome, go to Options>video devices.  Make sure that "Enable Skype Video" and "Start my video automatically when I am in a call" are selected.  For me there was only one selection available for the "select webcam" option.

Check video functionality in Skype by using the "test" window in this dialog box.

Close out of this dialog box.

Start Skype from Applications>Internet>Skype or a launcher.

Test the audio input using the Echo / Sound Test Service.  

**Notes:**

I was able to use "luvcview" application downloaded using Synaptic Package Manager to test the functionality of the webcam before I stumbled onto the Skype "options > video > test" function described above.

The quality of the webcam is much better than expected after seeing lots of posts about folks having problems with their cams.

When starting Skype, be careful not to get multiple instances of the application running.  Look up in the upper right and make sure you've only got one skype icon; if there's more than one, right click and quit the excess instances of the application.

**Closing:**

I would like to say Thank You to all who have given me a hand as I learn about Linux, from the Colorado Linux Users & Enthusiasts and also on the help forums.  I'm glad that I have finally had a chance to give something back to the Linux community.

  -AH

---

### Post by Andy H. on 2009-11-18
BTW - here's an example of what the webcam video quality looks like (captured using lucview).


[IMG]http://i49.photobucket.com/albums/f298/hornja/Gigaware_webcam_ex.jpg[/IMG]

---

