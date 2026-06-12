---
title: "K3B: Rip CD to FLAC"
date: 2014-07-31
forum: Multimedia Software
---

### Post by fballem on 2014-07-31
Hi,

I've been using ubuntu for several years - including the Unity Interface. I am interested in trying out Kubuntu 14.04 - the desktop is intriguing.

It is a steep learning curve, and I've been able to get most of the basics in place - sound is a nightmare.

The one issue that I have not been able to solve is to configure K3B so that I can rip a CD to FLAC. There is no FLAC encoder plugin - just Orb ,which I'm not interested in, since I strongly prefer a lossless format - disk space is not an issue.

Could someone please provide me with step-by-step instructions on how to do this?

I am comfortable using a terminal if that's required, but I get a sense that part of what KDE is about is to avoid the terminal as much as possible.

I will doubtless have other questions, which I'll ask through separate posts. This is a real issue to which I have not seen a solution, so any help would be much appreciated. I understand that Dolphin can be used, but the process is convoluted. In ubuntu, I have been using sound juicer and I assume that K3B is intended to operate in a similar fashion.

Thanks for your help,

---

### Post by Vladlenin5000 on 2014-07-31
Is there any reason for not using the software you're used to?

---

### Post by fballem on 2014-07-31
I like to putter. I do like ubuntu, but I am intrigued by the possibilities with KDE. There will be some challenges - KDE does things quite differently - but it is also quite mature. I took a brief look at OpenSUSE, but between RPM and how slow it is, I lost interest quickly.

---

### Post by Yellow Pasque on 2014-07-31
So do you have flac package installed?

Also, have you tried Audex?

---

### Post by fballem on 2014-07-31
The flac package is installed. There is a flac decoder, but there is no flac encoder. I could probably do it using the command line in the external encoder, but I don't know how to set it up.

I haven't tried Audex - I'll check into it.

---

### Post by fballem on 2014-08-01
I found the solution - quite by accident. It turns out that flac is not installed by default.

When I did sudo apt-get install kubuntu-restricted-extras flac the option to extract to flac was available in K3B.

---

### Post by SeijiSensei on 2014-08-01
If you do switch to Kubuntu, you won't need K3b to rip to FLAC once kubuntu-restricted-extras are installed.  If you insert a CD and open it from Dolphin, you'll see an array of folders that present the tracks in every supported format.  To rip tracks in FLAC you just drag and drop them from the CD's flac folder to your hard drive.  You'll have the option of ripping the entire CD or individual tracks in any format for which you have a codec.

---

### Post by fballem on 2014-08-01
Seiji:

Thanks for that. I'll have to figure it out - it definitely doesn't feel intuitive, especially when you have been using sound juicer in ubuntu. I've adopted the philosophy of "crawl, walk, run". I found the learning curve to be really steep when I switched from Windows Vista to Ubuntu some years ago. In those days, ubuntu was running Gnome 2. The switch to Unity was pretty easy - and I actually like Unity. It's just that I have been hearing about KDE for some time and I don't like to operate in ignorance.

Please take care, and thanks again.

---

### Post by Yellow Pasque on 2014-08-01
> **SeijiSensei said:**
> If you do switch to Kubuntu, you won't need K3b to rip to FLAC once kubuntu-restricted-extras are installed.

kubuntu-restrcted-extras shouldn't have anything to do with FLAC (it's not a proprietary/restricted codec). The flac encoder is what's needed, and it's not installed by default.

---

### Post by SeijiSensei on 2014-08-01
> **Temüjin said:**
> kubuntu-restrcted-extras shouldn't have anything to do with FLAC (it's not a proprietary/restricted codec). The flac encoder is what's needed, and it's not installed by default.

Actually I didn't think so either.  I was just going on the basis of what the OP reported.  FLAC is most certainly an open codec.  Is there some reason why it isn't shipped by default?  Must we live in a world where the encumbered MP3 codec gets installed by checking a box during Ubuntu installation, but FLAC does not?  How about Ogg?  I realize that MP3 is the dominant codec, but how are we going to move people into the open world if Ubuntu doesn't even ship the most common open codecs?

---

### Post by Yellow Pasque on 2014-08-01
> Must we live in a world where the encumbered MP3 codec gets installed by checking a box during Ubuntu installation, but FLAC does not?
That's not really accurate. The fluendo codec is not an encoder like lame and the default Ubuntu install does come with FLAC decoder (libflac).

---

### Post by SeijiSensei on 2014-08-02
I don't understand the logic of including only decoders.  I understand full well why encumbered software like x264 isn't included, but why only a FLAC decoder and not an encoder?  Surely the Ubuntu developers must know that many many users of their product will want to rip CDs.  I think Ubuntu should encourage the use of open technologies like FLAC and Ogg and make them as least as available as MP3.  I can get MP3 support by checking a box during installation, but I have to take extra steps after installation to get encoders for the other formats.  That's not a "level playing field."  If anything, I'd tilt the field in favor of the open technologies.

---

### Post by Yellow Pasque on 2014-08-02
> I can get MP3 support by checking a box during installation, but I have to take extra steps after installation to get encoders for the other formats.
Again, the Fluendo mp3 codec is not an encoder. Them main point of the checkbox is so that you can play mp3's in the Live environment or right out of the box. You have to take "extra steps" to install lame to encode mp3's.

---

