---
title: "Creating constant bitrate XviD files"
date: 2009-04-22
forum: Multimedia Software
---

### Post by MariusLV on 2009-04-22
Hi all,

For some time I have been trying to figure out some way to convert video to my [_Creative ZEN media player_]("http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999&nav=1"). The device is capable of playing WMV9, DivX and XviD, but the video must be encoded with constant bitrate, or playback will either fail entirely or be bugged to the point where you can neither search nor stop and resume playback properly.

My problem is this: I have yet to find a Linux-based piece of software capable of encoding constant bitrate XviD, DivX or WMV files. I had high hopes when I found Avidemux, but as far as I can see it does not offer the option of constant bitrate encoding for any of its supported output formats. I know that command-line Mencoder is supposedly capable of doing the job, but I would really like to be able to do things via a graphical user interface.

Is there anyone who can point me towards a solution to my problem?

/Marius

---

### Post by lovinglinux on 2009-04-22
Avidemux does offer constant bitrate. Select the "MPEG-4 ASP (Xvid4)" video profile, then click the configure button below it, then in the "Main" tab select "Single Pass - Bitrate".

On WinFF (which uses ffmpeg),  select "AVI", "Xvid in AVI" and put the desired bitrate in the additional options.

---

### Post by MariusLV on 2009-04-22
lovinglinux, thank you for your reply. However, I am afraid none of your suggestions worked. I previously did try exactly what you suggested for Avidemux, but found that this does not produce a playable file. Trying it again I also notice that, whilst encoding, the "average bitrate" number fluctuates around the target bitrate. This seems to me to suggest that your method does not in fact produce a strictly constant bitrate file.

As for WinFF, after doing what you suggested I clicked "convert", only to be sent to a terminal window that reported "Unknown encoder 'libxvid'", but none the less prompting me to press ENTER to continue, though doing this produced no effect apart from causing the terminal window to close, returning me to the WinFF GUI.

Thanks again, though :-)

---

### Post by lovinglinux on 2009-04-22
> **MariusLV said:**
> lovinglinux, thank you for your reply. However, I am afraid none of your suggestions worked. I previously did try exactly what you suggested for Avidemux, but found that this does not produce a playable file. Trying it again I also notice that, whilst encoding, the "average bitrate" number fluctuates around the target bitrate. This seems to me to suggest that your method does not in fact produce a strictly constant bitrate file.

I also notice that the bitrate fluctuates, but I was hoping it could work. Well, I guess you are right about this.

> **MariusLV said:**
> As for WinFF, after doing what you suggested I clicked "convert", only to be sent to a terminal window that reported "Unknown encoder 'libxvid'", but none the less prompting me to press ENTER to continue, though doing this produced no effect apart from causing the terminal window to close, returning me to the WinFF GUI.

Thanks again, though :-)

I guess you need to install restricted-extras.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kamitsukai on 2009-04-22
why not try Handbrake? that works with lots of portable video players =]

> [http://www.getdeb.net/app/HandBrake]("http://www.getdeb.net/app/HandBrake")

---

