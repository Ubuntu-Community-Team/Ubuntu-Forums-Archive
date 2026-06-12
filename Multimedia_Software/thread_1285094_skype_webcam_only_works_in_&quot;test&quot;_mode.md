---
title: "skype: webcam only works in &quot;test&quot; mode"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Ampi on 2009-10-07
I have a Logitech webcam (1 month old) which worked perfectly fine with Cheese and Skype until today. 
Today I was videocalling someone with skype when I decided to stop showing my video. When I clicked on "Show MyVideo" it decided to no show it anymore. 

When in Video Settings I click on "Test" to test the webcam I get a perfectly good video of myself and the light on the webcam goes on. 
But as soon as I close the settings and go back to the phone call the light of the webcam turns off and no video is shown. I have the option "Show MyVideo" during the call, but clicking on this doesn't make it work.
In Cheese my webcam still works fine, with light and all. 

I tried installing Skype 2.1 Beta, but more problems because I had no options in Audio Settings and couldn't make myself heard. So now I am back with Skype 2.0. 

The Webcam is USB and I tried different ports. All the same result. After all these changes I alse restarted the computer, nothing.

Output of lsusb
 ```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0805 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Does anybody have any idea how this suddenly changed and how to get it work again?

---

### Post by Subban on 2009-10-07
Did you try renaming the .Skype folder in ~/ to see if it is just a config issue, as it sounds like Skype may have just broke something in its settings. If it works then, its a config problem with Skype, if not then rename the .Skype folder back as its not the problem.

---

### Post by Ampi on 2009-10-19
The next time I logged in it suddenly worked again.. Maybe a temporarily change somewhere that needed reset...?

---

### Post by Subban on 2009-10-19
Anything is possible, glad its working again :]

---

### Post by respectirocz on 2009-10-20
I just had pretty much the same problem with Skype in Jaunty, I was running Skype 2.0 and all of a sudden today I could not send video, in the options under video devices the "test" was working a little funny and now not at all. 
I restarted and it was doing the same thing, then I went to skype's website, downloaded the newest v2.1 and things just got worse, I had no video and no sound. 
I uninstalled skype completely and found the installer that I downloaded way back when and I installed v2.0 again. So now I'm back to voice works video doesn't. 
By the way, when I use VLC to play capture device my webcam turns on and I can see myself no problem. 
I noticed in the "Video Devices" section of skype options it doesn't list my logitech cam like it used to but rather "UVC Camera"

---

### Post by Ampi on 2009-11-03
hmmm, that is exactly the problem I had, skype didn't even list my webcam, but now it works again, the only thing I did was restart the computer and log in again. So I don't have an answer for you. It kind of came radomnly and went radomnly.
I do have the same problem on my netbook, but there I get nothing working, not even cheese.
I hope someone can fix the problem for you..

---

### Post by MusJet on 2009-11-03
Hi ! If you are using 9.04, try:

sudo aptitude install ld.so.preload-manager
sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so

In terminal mode you can run "gstreamer-properties" and select defaults.

Cheers,

   Musjet

---

### Post by Ampi on 2009-11-03
I thought I'd try that too on my netbook.. ;)
But I can't do the second command, it simply says that the command ld.so.preload-manager doesn't exist...

---

