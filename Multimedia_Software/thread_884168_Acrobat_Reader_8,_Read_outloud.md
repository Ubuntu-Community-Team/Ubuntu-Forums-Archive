---
title: "Acrobat Reader 8, Read outloud"
date: 2008-08-08
forum: Multimedia Software
---

### Post by irv on 2008-08-08
When I write a document in OOwrite, I export it to a PDF file open it with Acrobat 8 and activate the read out loud. It helps me find mistakes in my writing. I could do this when in Windows, but not work in Ubuntu. It seems to load but no sound. I checked my sound in other programs and I have sound so it must be in a setting. I checked the setting in the reader, and the only option I have under Preferences>Multimedia is "RealOne(tm) Player". So I downloaded and installed Real Player 11 for Linux. It works and plays my sound files, but still no sound in Reader. Anyone got an idea what to do?
Thanks 
Irv

---

### Post by irv on 2008-08-10
I wrote this two days ago, and no one replied. Is there anyone else using Acrobat Reader 8 with the read outloud enabled? When you go into the preferences all the read-outloud features are grayed out. I know this is not in the repository and it might not even work with Ubuntu,and if that be the case I will go back to using kpdf with out this feature, but it would be nice to know that this is the case.
Thanks
Irv

---

### Post by mr.z on 2008-08-11
Same problem here..

I'm not sure if it runs through orca or similar accessibility software?

Got orca running and working but still nowhere on the pdf reader..

I'd be very happy to get it working myself.

---

### Post by oronte on 2008-10-08
Have a look at this: [http://www.linux.com/feature/55193](http://www.linux.com/feature/55193)

---

### Post by russelld on 2008-11-15
Acrobat needs to have acrobat-plugins installed to enable text to speech, and java script enabled.
I've never been able to get it going.

**[COLOR="Red"]Buyer Beware![/COLOR]**
[COLOR="Red"]If java script is enabled in  Acrobat 7+, it can phone home if the pdf has been tagged with Remote Approach,[/COLOR] 
[http://lwn.net/Articles/129729/]("http://lwn.net/Articles/129729/")

> Apparently, Remote Approach's "tag" to our document included the addition of JavaScript code causing Acrobat to report back to their server; the information reported includes the fact that the document had been read, our IP address, and which viewer it had been read in.

The same author tested tagged pdf with linux pdf readers and the pdf was still readable and didn't phone home.  

> Remote Approach's reporting did not work when we viewed the document with Kpdf, Xpdf and Adobe Reader 5.0.10. It also failed using Apple's "Preview" application on Mac OS X. The document was still viewable with no apparent glitch in other PDF readers, but the reporting function did not work

Linux has home grown pdf to speech readers in kpdf.  

I have a little script I use to render a pdf to speech which I can use on mp3 player.  Modify to suit your needs.

step 1
open kword, import pdf, save as txt

step two:
enter this into editor

```
#!/bin/bash
	# turn txt to mp3, rename files to mp3
	# and move them into seperate directories

NICE_LEVEL='-19'
OLD_FILE_SUFFIX='txt.wav.mp3'
NEW_FILE_SUFFIX='mp3'

for file in *
do 
 nice $NICE_LEVEL text2wave "$file" -o "$file.wav"
 nice $NICE_LEVEL normalize-audio "$file.wav"
 nice $NICE_LEVEL lame "$file.wav"
 rm -f "$file.wav"
done
	# Traverse list of files ending with 1st argument.
for filename in *.$OLD_FILE_SUFFIX
do
	#Strip off part of filename matching 1st argument,
	#then append 2nd argument.
 mv "$filename" "${filename%$OLD_FILE_SUFFIX}$NEW_FILE_SUFFIX"
done

exit 0

```

then same it somewhere like ~./bin/txt2mp3 
then make it executable
and run on a txt file
this will take some temp space on hard drive.  Can try another script that breaks up the file in chunks: [http://forums.gentoo.org/viewtopic-t-195579-highlight-festival+tips.html](http://forums.gentoo.org/viewtopic-t-195579-highlight-festival+tips.html)

It will take some time, chill out, have a break to pick up the mp3 later.

---

### Post by nortexoid on 2010-01-01
This thread is old and Acrobat is now at version 9, but I'm having this exact problem. It works fine in Windows, so I wonder what the problem is in linux. It would be nice if evince caught up with kpdf so that we wouldn't have to rely on acrobat in gnome.

---

### Post by Queixa on 2010-01-27
Here's what worked for me:

I had originally installed Acrobat by downloading the .deb file from Adobe.com and running the installation from that. I could not get the Read Out Loud to work.

 I went to the Synaptic Package Manager, marked the **Adobe Acrobat Reader** for complete removal, and marked "**Acroread**" for installing. After applying and starting Acrobat again, I heard voices! (The Read Out Loud feature worked fine, and I could choose between evice and festival in the Preferences.)

I'm too new at all this to know why this worked or if it will work for anyone else, but I don't think it will hurt to try.

---

### Post by Maximus_ARNP on 2010-05-04
Removed.

---

### Post by Talorgan on 2010-06-03
> **Queixa said:**
> I heard voices!

Do you really mean voices plural?

... because I seek text-to-dialogue software.

---

### Post by jackn on 2011-01-30
> **Queixa said:**
> 
 I went to the Synaptic Package Manager, marked the **Adobe Acrobat Reader** for complete removal, and marked "**Acroread**" for installing. After applying and starting Acrobat again, I heard voices! (The Read Out Loud feature worked fine, and I could choose between evice and festival in the Preferences.)



Thanks, Queixa.
Exactly same issue and your solution worked a treat. 

Couldn't get 'acroreader' from Synaptic, but 
```
apt://acroreader
``` 
typed into the Firefox address bar worked fine.
So, it is possible to use Acrobat to read PDF's (and thereby any web page) out loud in Ubuntu.
```
acroread
```
will then launch the reader.
jackn

---

### Post by ziemowitzima on 2011-10-27
Hi 
I am trying to read-out-loud working on ubuntu10.4 and acrobat 9.
I did everything I could find , but still my problem is not solved...
 I want to activate Read Out Loud when I click View -> Activate  Read Out Loud, it seems to load the document again however fails to read  anything.
 So I checked in Edit -> Preferences -> Reader
 All options for Driver and Voices were greyed.

Best

---

### Post by tuxuntu on 2012-05-28
I know this thread is old,
But some people might looking for this,

From [https://help.ubuntu.com/community/AcrobatHowTo]("https://help.ubuntu.com/community/AcrobatHowTo")
Linux acrobat reader read out loud

Enabling Read Out Loud
Adobe Reader has the ability to read text from PDF files out loud to the user. 

To enable Read Out Loud in Ubuntu please install the **libgnome-speech7** (GNOME text to speech library) package then run at the Terminal:

**sudo /var/lib/dpkg/info/acroread.postinst configure**

Open the desired PDF file and click View -> Read Out Loud -> Activate Read Out loud -> View -> Read Out Loud

and then choose either Read This Page Only or Read to End of Document.

Read Out Loud preferences are found by clicking Edit -> Preferences -> Reading


Cheers,

---

### Post by irv on 2012-05-29
> **tuxuntu said:**
> I know this thread is old,
But some people might looking for this,

From [https://help.ubuntu.com/community/AcrobatHowTo]("https://help.ubuntu.com/community/AcrobatHowTo")
Linux acrobat reader read out loud

Enabling Read Out Loud
Adobe Reader has the ability to read text from PDF files out loud to the user. 

To enable Read Out Loud in Ubuntu please install the **libgnome-speech7** (GNOME text to speech library) package then run at the Terminal:

**sudo /var/lib/dpkg/info/acroread.postinst configure**

Open the desired PDF file and click View -> Read Out Loud -> Activate Read Out loud -> View -> Read Out Loud

and then choose either Read This Page Only or Read to End of Document.

Read Out Loud preferences are found by clicking Edit -> Preferences -> Reading


Cheers,
I gave this a whirl and still no sound. Everything seemed to install and configure OK, but it still the read out loud will not function right.
Does it work for you?

---

