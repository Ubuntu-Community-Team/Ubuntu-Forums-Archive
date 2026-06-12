---
title: "mythbuntu install cd hangs checking master key"
date: 2012-08-08
forum: Mythbuntu
---

### Post by rusty0101 on 2012-08-08
I've been running Mythbuntu now for a good 5 years. Have a primary and secondary server running, only problem there is that the secondary server is having har drive problems causing the process to hang. Will fix once I've got money for a new hard drive.

What I'm running into as a problem tonight though has to do with building a new front end. I've experienced two distinct problems. The first is that the display that this system will end up using is a SD TV, not a high end monitor. The problem this poses is that I can't read a large number of the screens of the installer with this display. Fortunately I do have a spare monitor, that I'm using to continue on with the install, but it would be nice if the installer offered resolution options and testing to allow the user to select a display mode and setting that is readable, and doesn't require a monitor capable of 800x600 or higher to work. With the VGA adapter to the TV, I've had to set up systems with a 640x480 output, then set up Mythtv to use a resolution more like 520x380, and Hope that I can get it to center on the screen. Yes, I consider that annoying.

Second problem I'm running into is that the installer gets to the 'give me the key to your back end, and we'll test it.' I enter the key for the back end, and hit 'test', and the installer just sits there. No more updates on the installer of installation progress, no indication of success, or failure, nothing.

On the off chance (and I can't come up with a good reason for the chance to be correct) I'm downloading a 32bit ISO image and will try that to see if I can get further. The master back end is 32bit, I've been using it, and upgrading at LTS releases for the past 5 years after all. When I started 64bit wasn't even considered a reasonable possibility for a Home Theater Appliance. There's been a lot of great development. I do have other front ends that are talking with the back end just fine, including back-ends I installed pretty much the same way I've been working on this one.

Troubleshooting elements considered.
[LIST]
I have been able to ssh from the new front end to the back end.
I've re-verified that the back end and the installer are using the same 4 digit key.
I've got about 15 min to finish downloading the 32bit release ISO, at which point I'm checking that.
[/LIST]

-Rusty

---

### Post by rusty0101 on 2012-08-08
Ok, same problem with the 32bit release.

Going about this a bit differently, I've a mini.iso installer available. That said, someone really needs to tie down the package maintainer for the mythfrontend package and have a talk about **not** checking with the user to see if there is already a mythtv back-end server to connect to _before_ installing services like mythtv-backend, mysqld, Apache, mythweb, and the other asundry server packages that don't need to be installed for a front end, except some place in the user's network.

---

### Post by tgm4883 on 2012-08-08
> **rusty0101 said:**
> Ok, same problem with the 32bit release.

Going about this a bit differently, I've a mini.iso installer available. That said, someone really needs to tie down the package maintainer for the mythfrontend package and have a talk about **not** checking with the user to see if there is already a mythtv back-end server to connect to _before_ installing services like mythtv-backend, mysqld, Apache, mythweb, and the other asundry server packages that don't need to be installed for a front end, except some place in the user's network.

Those packages shouldn't be getting installed on a frontend only machine. You saw this on a fresh 12.04 frontend only install?

---

### Post by rusty0101 on 2012-11-05
I will have to check the mini CD before I can confirm, but I do know that the Mini was for either 11.10, or 12.04. I just don't remember if I had to do a version upgrade or not.

It has been one of my pet peeves about the Ubuntu MythTV packages for a long time though. If they fixed it for 12.04, great, but like I said in the first message, I couldn't simply install from the MythBuntu CD because I couldn't use the install platform on a TV. When the resolution of the device you are using is less than 640x480, and the lowest resolution the installer gives you is 800x600, it makes the installer very cumbersome to use, if it is possible at all.

It is up and running at this time, and on the LTS edition of Lulabuntu with the MythTV front end launched on boot. It's working, so I'm not fighting with it any more. Though I did give it the name Jouster as it replaced a system named Jester. Still the entertainer, just much more of a fighter.

---

