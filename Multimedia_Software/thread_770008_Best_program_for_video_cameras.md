---
title: "Best program for video cameras?"
date: 2008-04-27
forum: Multimedia Software
---

### Post by frup on 2008-04-27
I have had a video camera for over a year and that whole time I have been wanting to backup my videos on my computer (it has those mini tapes model: panasonic nv-gs27) The camera didn't come with a USB cable or dv cable but had the ports. Today I discovered my brothers nokia usb cable fits my camera and so we plugged the camera in to Ubuntu.

using luvcview we can access and even record avis from the camera, but they lack sound.

using kino and avidemux we can't even select/find the camera to capture from.

my question is how can I get these videos easily, with sound to have them backed up (I have 7 mini tapes and they're almost all full, would like to clear some) The sound should come over the USB connection too right?

cheers.

---

### Post by frup on 2008-08-16
After months with no solution I would like to bump this thread.

We now have a TV capture card with AV support, theoretically I should be able to record the input similar to how one would record to a VCR, what programs are available to interface with the TV card?

What is the best way to do this? We have mythTV and that is set up for basic channels but would like some help configuring it to record from camera.

This is really beginning to irritate me and I feel so stupid. If I met you in person I would probably use stronger language than that too.

---

### Post by Erlander on 2008-08-18
I'm far from an expert in this area and experience quite a few problems myself but since no one else has answered you so far here goes.

Kino should be able to grab your videos direct from the camera through the usb port.  Since you say you are using mini dv tapes I'm guessing that you have a digital camera.  If your camera and pc both have a firewire port (1394) then it may be a better option.

However Kino does have some problems getting it going.  Try searching this forum and the "multimedia Production" forum for Kino and you should get the answers.

Details of your setup and the camera should also help others give you more detailed assistance.

I don't think you need the capture card and if you can grab as dv and not analogue you will get better quality.

Rob

---

### Post by eggdeng on 2008-08-18
As Erlander says, Kino is a good option but it doesn't support usb. So you can only use it if you have firewire. These days, it's fairly straightforward to set up and pretty much bug-free.
```
sudo apt-get install kino
```
Start Kino from the menu _with the camera plugged in and turned on_. You will get a message about /dev/raw1394. [The name may differ slightly].
Run```
chmod 777 /dev/raw1394
``` & you should be good to go.

---

### Post by remeeraz on 2008-10-14
> **eggdeng said:**
> As Erlander says, Kino is a good option but it doesn't support usb. So you can only use it if you have firewire. These days, it's fairly straightforward to set up and pretty much bug-free.
```
sudo apt-get install kino
```
Start Kino from the menu _with the camera plugged in and turned on_. You will get a message about /dev/raw1394. [The name may differ slightly].
Run```
chmod 777 /dev/raw1394
``` & you should be good to go.

That chmod command is not gona work. If it does, it won't the next time you boot.

Kino is a great program for vid capture and editing through Firewire, and if you want to get firewire to work propperly, try my instructions on the following thread.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

---

### Post by DuncanNZ on 2009-02-23
> **eggdeng said:**
> Run```
chmod 777 /dev/raw1394
``` & you should be good to go.

This should go with a security notice, see here: [https://lists.ubuntu.com/archives/ubuntu-devel/2006-March/016593.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-March/016593.html)

Please remember this issue when considering this solution.

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

