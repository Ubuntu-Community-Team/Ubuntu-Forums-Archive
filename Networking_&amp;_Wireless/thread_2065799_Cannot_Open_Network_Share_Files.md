---
title: "Cannot Open Network Share Files"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by ez31011 on 2012-10-02
I am having an issue opening files on a shared drive/folder. I have 3 computers on a Workgroup (Samba running on the 2 Ubuntu machines):

1 XP Laptop
1 Lubuntu 12.04 Laptop
1 Ubuntu 12.04 (64) Desktop

There is a NTFS external drive connected to the Ubuntu Desktop that I want to share across all the computers. At the moment the XP Laptop can open the files on that drive, but the Lubuntu Laptop cannot. 

I can browse/explore the files using the Lubuntu laptop, but I cannot open them. However the Lubuntu Laptop will open files on the XP Laptop. 

There are various files (music, videos, pdfs, etc). The only clue I get is that when I try to open a pdf file the document viewer returns this error:

Unable to Open Document. Failed to mount Windows share.

If I try to open a music or video file it's as though there is no content. And opening an image shows just a white screen. Hopefully that all makes sense.

Any input would be great, Thanks.

-Chris

---

### Post by SteveDee on 2012-10-17
> **ez31011 said:**
> ...I can browse/explore the files using the Lubuntu laptop, but I cannot open them. However the Lubuntu Laptop will open files on the XP Laptop....

Can you clarify something, using the Lubuntu laptop can you open files on the internal Ubuntu hard drive?

---

### Post by ez31011 on 2012-10-17
I can not open them remotely. using my Lubuntu laptop I can view and explore the shared drive on the Ubuntu desktop. I can also add and remove files from that drive, the only thing I can't seem to do is open them remotely from this one computer. 

For example when I attempt to open an audio file (I've tried Audacious, VLC and Mplayer) it appears as a song with the length of zero seconds. 

Once again I can open these files remotely using a Windows XP laptop.

I hope that clarifies the issue I'm having. Thanks again for any help/direction you can pass along

---

### Post by SteveDee on 2012-10-19
> **ez31011 said:**
> I can not open them remotely...

There are many variables that may affect this, so I've just configured 2 laptops with a USB stick to simulate your hard drive.

I realise this is not a direct equivalent to your setup, but I hope it might help you. If not, I can probably change a few things.

My configuration:-
 2 x Lubuntu laptops
The "server" is running 12.04
The "client" is 11.04

Lubuntu is a light-weight Linux distro, so you may find there are packages missing which are required for proper network operation. Consequently, both of these laptops have been set-up for networking using the method I've detailed here: [http://captainbodgit.blogspot.co.uk/2012/10/networking-with-lubuntu-win7-and.html](http://captainbodgit.blogspot.co.uk/2012/10/networking-with-lubuntu-win7-and.html)

On the "server" (the one with the locally attached external drive) find device details. In terminal type:-
```

sudo blkid

```

Somewhere on the output should be a line with your external device, in my case:-
```

/dev/sdb1: LABEL="STEVE8GB" UUID="80E9-471E" TYPE="vfat"

```

Now open /etc/fstab as root and add a new line at the end:-
```

UUID=80E9-471E /media/STEVE8GB/Music vfat

```
...only use your drive details.

Open Samba gui (start > System Tools > Samba

Create a share:-
```

/media/STEVE8GB/Music Read/Write Visible

```
...and via Samba share Properties set Access: Allow access to everyone.

Open PCManFM file manager > Tools > Open current folder as root

Navigate to /media/STEVE8GB (or wherever your drive is mounted)
Right click on folder > Properties > Permissions
Set Access Control: Other: Read Only

I suggest you reboot both computer (sometimes network access seems to take a few moments longer than it takes just to launch the desktop).

Now with my setup I can open/play music files on my remote client using VLC.

I hope this is helpful.

---

