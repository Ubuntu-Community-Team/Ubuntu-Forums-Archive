---
title: "Problem syncing Creative Zen Vision M"
date: 2009-12-28
forum: Multimedia Software
---

### Post by svivian on 2009-12-28
I have a Creative Zen Vision M mp3 player. I used to use gnomad2 to add music to it, but I just tried it for the first time since installing Ubuntu 9.10 and it doesn't seem to work.

When I plug in the device, Ubuntu recognises it as a media device, under `gphoto2://[usb:001,009]/`.

When I try to open the Music folder on the device, I get the message: "Sorry, could not display all the contents of "Music": Failed to get file list: -8: Fixed limit exceeded"

Opening Gnomad2 gives the message: "No jukeboxes found on USB bus."

Any idea what the problem could be?

---

### Post by Jimtheplanner on 2009-12-29
OK

This is whats up!!!

When you plug in your Zen it mounts on the desktop then when you open Gnomad2 it cant mount whats already mounted.....

So you must plug in your Zen then when the icon appears on the desktop right click and "unmount" it. Once done the you can open Gnomad2 and it will work for now.

Season best wishes

Jim

---

### Post by svivian on 2009-12-29
Thanks, it works!

I did install Banshee and it seemed to recognise the device OK. However, everything in my music collection came up with incorrect tags and so on. For example, the 8th track of "100th Window" by Massive Attack is listed as being by Gnarls Berkley for some reason. Any ideas?

---

