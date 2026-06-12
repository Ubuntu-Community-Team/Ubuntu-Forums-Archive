---
title: "Opening Powerpoint pptx Files with Embedded Video and Sound - Solved"
date: 2014-01-15
forum: Multimedia Software
---

### Post by West Swan on 2014-01-15
Hello,

I think I have posted this in the right section.  If not please feel free to move it :)

In 3 months time Microsoft will be ending support for both Windows XP and Office 2003.

At this time people can either upgrade to a later version of Windows or upgrade to Linux.

For those with lower specced machines, Lubuntu would seem to be a very good choice.

With this in mind I have been testing Lubuntu 13.10 on an old laptop of mine and for the most part it does everything I want.

There is one significant exception though and that is the ability to open and play pptx powerpoint presentations.  That is a must for me and I would think for a lot of other people as well.

I for one won't be asking my friends and co-workers to send the files in a different format.  I also don't want to have to go through the hassle of converting them myself.

So what I did was test the 6 programs below to see if they could open and play this file (see link): [COLOR=#0000cd]http://medicine.hsc.wvu.edu/Biochemistry/Education/Undergraduate/BIOC-339-Summer[/COLOR]

The pptx file link I am talking about is the second one which is about a third of the way down the page.  The embedded video is in slide number 4 of this pptx file.

I tried the latest stable versions of:

pptviewer, calligra stage, libreoffice impress, powerpoint viewer 2010 in wine, apache open office and kingsoft presentations.  

Some didn't even open the pptx file.  Others opened it but did not recognise the video component.

The only program that opened it and allowed playing of the video with sound was Kingsoft Presentations which is part of Kingsoft Office Free version.  It is currently in beta I think.

Now this isn't open source and I think if you are from the U.S. it is illegal for you to use it - no idea why.  It is from a company in China I believe.

So for my part I will be getting rid of all the other Office Programs and giving Kingsoft a try.

I can finally 'easily' open all the major MS formats by default.  Of course Kingsoft can be installed on other Linux distros as well.

Does anyone know if there are any other programs that will open this specific pptx file that are open source?

Cheers,

Paul

---

### Post by cmcanulty on 2014-06-29
I have tried it in ubuntu powerpoint viewer, powerpoint viewer in wine, impress,and kingsoft. No luck in any of them. I can get sound in my win 7 virtualbox. I need them to play with sound in xubuntu14.04. I need this for a library patron.Please tell me how you got one to play in kingsoft.

---

### Post by Vladlenin5000 on 2014-06-29
Sound (and video) always depend on system-wide (and software-agnostic) codecs. As such, even if a certain software is capable of handling such format it might not be able to reproduce the embedded video, audio or both due to the absence of the codecs.

Have you already installed the additional (non-free) codecs provided by the ubuntu-restricted-extras package? If not please try again after installing the aforementioned package (note: there are specific packages for Kubuntu and Lubuntu and they're named accordingly).

---

### Post by cmcanulty on 2014-06-29
I have xubuntu restricted extras installed on xubuntu 14.04 should I install the ubuntu and kubuntu restricted extras's too?

---

### Post by Vladlenin5000 on 2014-06-29
> **cmcanulty said:**
> I have xubuntu restricted extras installed on xubuntu 14.04 should I install the ubuntu and kubuntu restricted extras's too?

No need. The one you already have should cover the vast majority of your needs. However, there's nothing preventing the creators of a given presentation to use video and/or audio coded with some exotic proprietary codec we simply can't use in Linux, at the moment.

---

### Post by Jorge_Arce_Ortiz on 2015-01-29
I have the same problem. Powerpoint (running on PlayonLinux) crashes on Lubuntu 14.04.1 every time that I try to play the video. But that video can be played with the stock video player opening the ppx file with the file manager and clicking on it (remember that pptx files are zip files). That is not a solution, regarding that a presentation is intended to be seamlessly continuous.

---

### Post by DeMus on 2015-03-15
Hi guys, to make Libre-Office Impress play sound and video in powerpoint files, and yes, it also works on the examples shown by West Swan in his openinge message, is to install a package called Libreoffice-avmedia-backend-gst. Install it, don't really know if it is necessary but reboot and play the files with sound and video.
I also tried to use it in the Kingsoft WPS suite, but no luck. For some time I had e-mail conversation with one of the programmers in China, send him an example of a file which could not be played with sound, told him what I had done so far, but somehow the conversation stopped. Maybe it is too difficult.
WPS looks pretty good to me, so I was interested in using it, but for now I stick with LibreOffice..

---

### Post by valerietheblonde on 2015-11-21
I'm running xfce Debian Jessie but responding to this thread since it is currently the top-ranked search result in DuckDuckGo. For my particular powerpoint (pptx) with m4a audio, the libreoffice-avmedia-backend-gstreamer package was already installed, but the audio was not playing. The media icon within the powerpoint and the media player in Impress were visible and functional. After installing libreoffice-avmedia-backend-vlc the media icon became a questionmark but the audio was played correctly.

---

### Post by cmcanulty on 2015-11-21
my synaptic can't find libreoffice-avmedia-backend-vlc where did you get it?

---

