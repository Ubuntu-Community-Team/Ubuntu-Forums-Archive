---
title: "Sony ICD-UX91F Digital Voice recorder"
date: 2009-05-14
forum: Multimedia Software
---

### Post by sakusa on 2009-05-14
Just tested this on 9.04 - seems to work fine so far.It both records and plays back mp3 files natively, without any conversion whatsoever. Specifically it doesn't need any software installation - they seem to only support Win/Mac :mad:

Some of the other Sony models have either proprietary 'triple rate codec' recording or their latest LPEC/ Linear PCM ultra hi-fi. Too painful trying to convert them for immediate recognition.

It comes with a built-in USB stick,and was immediately recognized by Movie Player, which you can change to Rhythm Box etc. 

While connected to the PC, the file's ID tag can be edited in either File Browser or Rhythm Box, and it shows up on the microscopic LCD screen.

It's highly sensitive to noise, and speaker output volume is low, but headphone volume is fine.

---

### Post by corq on 2009-05-26
Thank you! I've steered clear of Sony recorders due to years of experience with them almost always requiring special software, codecs in Windows, let alone be Linux compatible. 

I just bought an RCA VR5220 (Audiovox actually) that I'll be returning, windows alerts to it being a flash drive, but appears defective as even the RCA/Audiovox software cannot detect it. Nothing shows up in Ubuntu under lsusb queries or anything. 

Your post of your experience was VERY helpful. Thank you!

---

### Post by sakusa on 2009-05-27
Hi corq - thanks for your response! Delighted to have been of some help. :-)

---

### Post by giddy1945 on 2009-06-05
Hello,
I just bought  the RCA VR5220, and I am having the same problem.  I do not want to take it back.  I want to make this work.  Please help.  Thanks.

---

### Post by exXplode on 2009-06-17
Hi there! I have no solution to you problems but a remark for everyone who finds this thread on google etc.:

There are Sony digital voice recorders that work well together with a GNU/Linux System: Sony ICD-SX800 and ICD-SX700

I own a SX800 (with 2 GB) and it works well.

The reason it works out of the box: It just shows up as mountable device (such as usb memory stick) and you can select uncompressed Wave or MP3 encoding, so your files will have a standard output format.


The software provided by Sony however, the Digital Voice Editor, will not run on Linux, but I do not need this piece of code!

Greetings, phil

---

### Post by laeltucker on 2010-01-29
> **giddy1945 said:**
> Hello,
I just bought  the RCA VR5220, and I am having the same problem.  I do not want to take it back.  I want to make this work.  Please help.  Thanks.

I just got one of these, and I figured out the voodoo to make it work under ubuntu!

When you plug this thing it, it looks like a usb thumb drive. Go find the .VOC files on it after you plug it in, and copy them off somewhere (they have names like A0000001.VOC)

Download the file devoc.c (hopefully the url will post right):
[http://www.cybercom.net/~dcoffin/rca/]("http://www.cybercom.net/%7Edcoffin/rca/")

(if the URL above gets munged just look for "devoc.c decode VOC" on google and check out the cybercom.net link)

apt-get install sox libsox-fmt-all

gcc devoc.c -o devoc
(and put the binary file in your path somewhere)

devoc -c A0000001.VOC > output.raw

play -t raw -s -2 -r 8000 output.raw

or, to convert it to a useful format (wav/ogg/etc):

sox -t raw -s -2 -r 8000 output.raw out.wav

---

### Post by laeltucker on 2010-01-29
I should add that I am running this all under Jaunty.

---

