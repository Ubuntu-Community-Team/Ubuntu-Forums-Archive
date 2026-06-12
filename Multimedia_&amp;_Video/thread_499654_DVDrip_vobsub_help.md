---
title: "DVD::rip vobsub help"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by Peregrine88 on 2007-07-12
I'm pretty new to linux. I installed dvd::rip like the ubuntu documentation instructed me to.

When I pressed the "Read DVD table of contents" to start the process it had an error reading this:

Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.

To state the obvious I do have a DVD in the drive. I checked the settings and found this:

rar command (for vobsub compression): rar-2.80 not found : NOT Ok

Did I miss something? How do I correct this error? One important note might be that I can't play the DVD either. I may be missing some important part. Any help would be welcomed.

---

### Post by Gen2ly on 2007-07-12
Pretty crazy.  Look maybe at this page will help:

[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)

---

### Post by bennyj on 2007-07-13
> **Peregrine88 said:**
> I'm pretty new to linux. I installed dvd::rip like the ubuntu documentation instructed me to.

When I pressed the "Read DVD table of contents" to start the process it had an error reading this:

Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.

To state the obvious I do have a DVD in the drive. I checked the settings and found this:

rar command (for vobsub compression): rar-2.80 not found : NOT Ok

Did I miss something? How do I correct this error? One important note might be that I can't play the DVD either. I may be missing some important part. Any help would be welcomed.

Did you check to see if you have the correct dvd player assigned under preferences? I have two dvd roms on my comp...the reader is /dev/hdc and the writer is /dev/hdd. sometimes it will not be picked up correctly with the defualt /dev/dvd. if you have only one reader and writer make sure that is the one selecter under preferences.

---

### Post by Peregrine88 on 2007-07-15
Yes, I had the right drive setup.

I finally figured out the what the error was, vobsub enables you to rip the subtitles of the dvd. I'm not really interested in the subtitles so the solution was to just continue. Just thought I'd post this clarification for anyone else that might be interested.

---

