---
title: "[Tutorial] How to set up Creative X-Fi in Ubuntu."
date: 2008-11-09
forum: Multimedia Software
---

### Post by Suilenroc on 2008-11-09
The following is a post I made on another forum ([www.overclock.net](www.overclock.net), specifically), but I think that I should probably put it here too. It's a tutorial regarding how to set up X-Fi in Ubuntu with the newly released drivers. It's made for new users, so forgive the low level of technical detail. Hope you like it!

---------------------------------------------------------------------------
There's been a few people around the net who have been looking for a tutorial on how to install the new creative drivers in Ubuntu. I decided to make one myself, rather than wait for someone else to. I'll be pointing people to this, feel free to do the same yourself.

First off, you'll need to download the new creative driver set off of the creative wesbite.

[http://support.creative.com/](http://support.creative.com/)

From that site, navigate to your sound card. Mine is the "x-fi elite pro."

Click "Download" below the driver, currently version 1.00, and accept the license. It will download a package in the .tar.gz format. When prompted by the download manager, click "open file." Extract the folder to your desktop.

Now, open up a Terminal. (Applications -> Accessories -> Terminal), and type in:
Code:

 cd Desktop

That cd's you, or moves you, into the selected folder, in this case, the Desktop.

Then, type in:
Code:

 ls

That displays all files on your desktop. You will then have to type in:
Code:

 cd *yourfilenamehere*

for me, it was:
Code:

 cd XFiDrv_Linux_Public_US_1.00

that takes me into that folder.

Now, you will have to run this as root. If you haven't yet set a root password, or if you don't know what a root password is, do this:

Code:

 sudo passwd

This then asks you for your user password. Put that in. It then asks for a "New Unix Password." Type in whatever password you want, I have it the same as my user password. Enter it a second time when promped.

Now, back to the installation.

You gotta get into the superuser mode, which is easy enough. Type in:

Code:

 su

Then, type in your superuser password, which we just set.

Now, just type this in:

Code:

 make

This will compile the program. Give it a sec to a few minutes.

Waiting... Waiting... Waiting...

DONE!

Now, just type in:

Code:

 make install

This should take a moment. After that, you're done! The drivers are installeD!

All that awaits now is to change your sound options to use the new driver. Go to: System -> Preferences -> Sounds.

Change all the entries there to your sound card. Mine looks like this: "Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS)"

After that, enjoy your card.

-Suilenroc



Post any questions to this thread, and I'll try to answer them.

---

### Post by Aldyrin on 2008-11-09
Have you gotten the multichannel analog outputs (5.1) on your card working?  I installed the driver and now I have stereo sound, but I don't see an option for surround in the mixer.

---

### Post by Suilenroc on 2008-11-09
I'm relatively certain that these drivers don't yet have the option of 5.1 output. Really, I'll take whatever I can. The sound quality is great, and that's just one of the last few things I need to switch to full-time linux use. 

(Next is iPhone syncing. If anyone knows this, please tell me.)

---

