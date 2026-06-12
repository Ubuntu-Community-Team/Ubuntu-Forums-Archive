---
title: "Can't video chat on any software"
date: 2010-01-04
forum: Multimedia Software
---

### Post by Moustaffa on 2010-01-04
Hi,

I have a very annoying problem: I can't seem to be able to video chat. Not on aMSN, not an Skype...
I'm sure that my camera works because I can take pictures using Cheese. However, when I establish a connection on aMSN or Skype, the other person only sees a white screen instead of my face.
(I've already installed farsight2)

My webcam is a Hercules Classic Silver.

Hope someone can help!

Greets

---

### Post by inobe on 2010-01-04
when you run a video test in skype' can you not see video ?


please leave the make and model of your cam on next post.

---

### Post by Moustaffa on 2010-01-04
> **inobe said:**
> when you run a video test in skype' can you not see video ?


please leave the make and model of your cam on next post.

No video in test chat. I only see a pop up window and hear a woman talking to test my mic settings (which doesn't work either, although I have a mic inside my camera).

When going to Option > Video Devices and press "Test", I get a scrambled image of colored lines (which is a good sign in some way, because before I had Farsight2 installed it was simply black).

About my camera: i ran lsusb in Terminal and this is what I got

Bus 002 Device 002: ID 06f8:3004 Guillemot Corp. 

If that doesn't suffice, here's a link to a site with more specs

[http://www.hercules.com/nl/webcam/bdd/p/22/hercules-classic-silver/](http://www.hercules.com/nl/webcam/bdd/p/22/hercules-classic-silver/)

Thank you for your help!

---

### Post by inobe on 2010-01-04
[http://ubuntuforums.org/showthread.php?t=1020873&highlight=Hercules+Classic+Silver](http://ubuntuforums.org/showthread.php?t=1020873&highlight=Hercules+Classic+Silver)

it may take a little work to get it going, read threw that thread before going forward.

a side note: logitech quickcams work out of the box, no drivers, no hassle.

---

### Post by Moustaffa on 2010-01-04
> **inobe said:**
> [http://ubuntuforums.org/showthread.php?t=1020873&highlight=Hercules+Classic+Silver](http://ubuntuforums.org/showthread.php?t=1020873&highlight=Hercules+Classic+Silver)

it may take a little work to get it going, read threw that thread before going forward.

a side note: logitech quickcams work out of the box, no drivers, no hassle.

Oh the irony :-) I found that earlier but it used to give me errors. Right after I posted my previous reply I gave it another try and guess what: it messed up everything!

For some reason my computer didn't play sound and video anymore (youtube, movies on computer, music, ... nothing worked). After rebooting those things worked again, but now my cam doesn't even work!
It used to work with Cheese, but now Cheese doesn't recognize the cam...

---

### Post by Moustaffa on 2010-01-21
Nobody that has the answer to this problem?

---

### Post by mn_voyageur on 2010-01-21
The Skype Test call is under Audio, on my version.  It only tests the audio portion of the call.  It should echo back what you say after the "ding."

The video test checks video.

what happens when you command line: lsusb

MN

---

### Post by Moustaffa on 2010-01-21
> **mn_voyageur said:**
> The Skype Test call is under Audio, on my version.  It only tests the audio portion of the call.  It should echo back what you say after the "ding."

The video test checks video.

what happens when you command line: lsusb

MN

I have a mic in my webcam, but when I speak after the "ding" it doesn't repeat it back, so my speaking wasn't registered.
When I go to video devices and click Test I see a scrambled screen full of coloured lines.

However, Cheese works fine, I can take pictures and all that.
Also I tried webcamming through a chatsite, and the webcam worked fine there as well (fluent image!).
So I really don't understand why it won't work over Skype and aMSN...

lsusb gives me the device when it's connected, no problem there.

---

