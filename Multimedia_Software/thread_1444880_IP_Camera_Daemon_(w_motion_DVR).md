---
title: "IP Camera Daemon? (/w motion DVR?)"
date: 2010-04-01
forum: Multimedia Software
---

### Post by KamakazieX on 2010-04-01
I believe I had a break in attempt today and would like to beef security up in the home. I want to motion sensor up the garage. I currently have some decent horsepower being underutilized as a ClarkConnect router, replacing with Ubuntu and adding some sort of IP Camera daemon. Camera's I was looking at include Linksys WVC80N and some commercial grade Panasonic IP cam's since I know a dealer.

What (OS?/FREE) options are available for the server side?

Hardware is pretty powerful:

Intel Atom with GCLF2 board, 1 GB ram, 120GB 2.5" SATA2 in a Travla case. Dedicated Linksys WAP5500N commercial grade N Access point with POE Gig-e port to wired network. Gig-e copper to an unmanaged netgear switch from the router hardware.

I had two goals in mind, motion detection and notification (For example a rule 9:30AM to 4:00PM M-F motion email notifications)
and an option to upload to the cloud.. then there is no hiding the DVR! Probably need the capacity for one camera, at a max of three- front entrance, rear entrance , and entire garage.

---

### Post by kblood on 2010-04-04
With Karmic, I was playing around with "motion", a package available in the Ubuntu repositories.
It was very easy to set up, and was working quite well when I tested it.

Now I have upgraded to Lucid, and it's giving me some issues, but maybe it's my super cheap crappy webcam.

Give it a try, it's quite easy to set up.
And once you have it running, for uploading to the "cloud", you could get Dropbox, and make "motion" save its files into a Dropbox folder.

---

### Post by oregonbob on 2010-10-16
I have security needs too because I live in a remote area. I have 4 Linksys netcams setup and it works pretty well for remote viewing. I have also installed Homeseer home automation software on a Windows box along with an X10 controller. I use a driveway alert and motion sensors to tell me someone is there via email and SMS on my iPhone. My home is secluded with a 1/2 mile long driveway. I get an email/SMS notice on my phone within 20 seconds of a vehicle entering my property. Then I also have motion sensors all over my home. I can activate them from my iPhone. They will email/SMS me if they detect motion.

The only hurdle I have not figured out is how to simply start recording from a netcam for a certain period of time *if* motion is detected. The cams have built-in motion detection but that has drawbacks of false positives and limited recording interval.

You should explore low cost X10 controller and motion sensors. There are a number of linux X10 daemons too.

If I could only find a vlc command, or any stream capture that I could start and say run for 2 minute intervals, save output to file for later viewing. They say vlc can do it, but so far I haven't been able to get it to work, so many confusing options.

---

### Post by RBLevin on 2010-11-04
kblood, is Motion in the Software Center? I can't find it ...

---

### Post by joeinbend on 2011-03-08
Extremely old thread here, but in response to the OP and oregonBob as well, ZoneMinder is probably a good solution for both of you. It's very flexible with the type of cameras it will accept, and you can do all kinds of remote triggering and notification functions with it. For Android users, there's even an app out there that will let you see your camera feeds with one click ("IP Cam Viewer Lite"). I've been using ZoneMinder for years, and been very happy with it. I also live on a large property out in the country, and it's great peace of mind to keep an eye on things remotely, and be notified if there's any activity.

---

