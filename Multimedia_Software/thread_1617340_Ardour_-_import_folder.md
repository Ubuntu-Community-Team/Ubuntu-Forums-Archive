---
title: "Ardour - import folder?"
date: 2010-11-09
forum: Multimedia Software
---

### Post by demonboy on 2010-11-09
Hi,

I'm new to Ubuntu (ex-Windows user) and new to Ardour. I used to use Adobe Audition/CEP. One feature I liked was to have my library of imported files outside of the multi-track and then just drag them in when I needed them. When I import in Ardour they are immediately added to the multi-track. Anyone know how I can do like I did in Audition?

Thanks in advance.

---

### Post by PipeManMusic on 2010-11-09
In the import dialog there is an option along the bottom about how the Audio is imported. If you set that to only import the audio as a region it will show up in the region list at the right of the main editor window and can then be drag and droped onto the editor time line.

You might try your hand at using IRC. There is a great channel on freenode #opensourcemusicians where a lot of friendly audio people hang and and talk about such things.

Also, I host a show called "The Open Source Musician Podcast" that is available at [http://opensourcemusician.libsyn.com](http://opensourcemusician.libsyn.com)

Hope this helps.

Edit: the actual option is to turn off "Copy files to session"

Daniel Worth

---

### Post by PipeManMusic on 2010-11-09
duplicate deleted

---

### Post by PipeManMusic on 2010-11-09
duplicate deleted.

---

### Post by demonboy on 2010-11-10
Hi Daniel, thanks for your reply. I see the drop-down, thanks. I thought I'd have a quick play and try and import an mp3 but it won't allow me. Do you know why? Also could you recommend a good guide to learning Ardour? I only need the basics for creating multi-track wavs for editing podcasts. 

Currently downloading your latest podcast, cheers.

---

### Post by PipeManMusic on 2010-11-10
In general Ardour doesn't support compressed audio import. The reasons and exceptions are this;

Reasons:
1. Those formats are not ideal for production as their quality degrades with conversion on import and again on export.
2. Most formats have questionable legality with regards to patens.
Exceptions:
1.Ogg - this is the only lossy format Ardour supports and it is a free format support by the software Ardour uses.
2.FLAC - this is a lossless compression format that makes audio files a little easier to handle but is also a free format.

The specific reasons MP3 isn't supported are:

1. It is a lossy compression format.
2. It has patents on it that give it questionable legality in a free software project.

Dan

---

### Post by demonboy on 2010-11-10
Hi Dan, thanks for the explanation. Whilst I understand this in principle I don't agree with it in reality. I'll give you an example:

In my most recent podcast I was sent audio recordings from a primary school. The person who sent it did her best but was obviously using some simple software where her recordings were outputted in mp3 format. This isn't her field, after all, so she sent what she could. In another example I could set my podcast recorder to record mp3s instead of wavs should my SD card be running short on space.

Audacity would be able to import these files no problem, so I guess I have two options:

1. Convert the mp3 to a file format that Ardour recognises. A bit of a bore. Any recommended bits of software for this?

2. Use another opensource multi-track recorder. Maybe Ardour is not what I require since I am simply cutting, aligning, fading, normalising wav files. Any suggestions?

I suppose a third option would be to run Audition under Wine. I've no idea if this will work. 

At the moment I have dual boot but I want to migrate from Windows completely.

Any further comments? Perhaps I should start another thread?

---

### Post by Pla1n on 2010-11-10
Audacity is available for Linux too.
Check the repositories or 
[http://packages.ubuntu.com/search?keywords=audacity](http://packages.ubuntu.com/search?keywords=audacity)

Otherwise you can use sound converter(also repos) or any other.

Seems like Audition does not work under wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5869&iTestingId=15857](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5869&iTestingId=15857)

You better be probably end up using Ardour and convert your audio as it is much better than
Audacity on Linux.

---

### Post by demonboy on 2010-11-10
My apologies, I'm getting my apps muddled up. I use Audition, not Audacity. I tried Audacity for Windows and was very disappointed. I found it extremely frustrating to use and lacking a lot of basic functionality, so unless the Linux version is different to Windows it's not going to work for me.

I think you are right to stick to Ardour. I'll just do some converting of file formats when I have to. Thanks for the help.

---

