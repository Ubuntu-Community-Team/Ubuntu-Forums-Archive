---
title: "Format an unformatted iPod in Ubuntu 10.10"
date: 2011-03-15
forum: Multimedia Software
---

### Post by cossintan on 2011-03-15
So the other day I plugged my iPod shuffle into my pc while booted into Ubuntu.  I couldn't access it through rhythmbox, so I mistakenly figured the best thing to do would be to format it with the fat system.  Big mistake.  It ended up turning out an error saying something along the lines of not being able to format the iPod in a 32 bit format.  Now my iPod doesn't show up at all, and I have no clue where to go from here to get it formatted and set up for use with rhythmbox.  Any help or advice would be greatly appreciated.  <3 you guys!

---

### Post by Chronon on 2011-03-15
The simplest thing is to find someone with iTunes and restore your device with that.

---

### Post by johntaylor1887 on 2011-03-15
Or install windows in virtualbox to do a restore.

---

### Post by cossintan on 2011-03-16
Ok, cool.  I didn't know if there were some cool terminal commands or something that could help out...

---

### Post by Chronon on 2011-03-16
Historically, iPods have a hidden RAW partition that contains the firmware and a FAT32 partition for the data.  You can manually write the appropriate MBR and create a new file system in the data partition (there are instructions for doing this in in Linux in Rockbox's wiki -- search for "manual restore iPod").  However, I don't know as much about the Shuffle as I have never owned one and it is not a model that's supported by Rockbox.

The Rockbox wiki also lacks a copy of the MBR for the Shuffle, so you would have to obtain one elsewhere.

In the end it will be much easier to just find a machine that has iTunes and use that to restore.

---

