---
title: "VHS(VCR) to mpeg (DVD)"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by graveson on 2006-11-05
I need to transfer a load of VHS tapes to mpeg format and i am looking for a solution for this that works without too much hassles on linux (Dapper). I do not want to go out and purchase a windows system just to copy some vhs tapes and enhance the quality. can anyone provide any ideas - hints

---

### Post by Jason_25 on 2006-11-05
Well to do this on windows, like everything else you would have to pay for some awful commercial software to do it.

A fairly easy way to do this would be to use ffmpeg to capture straight from a video device and encode to mpeg.  You have a few choices for capture devices.  I have an ATI TV Wonder Pro and it works flawlessly with dapper and edgy for cable.  I would assume the auxiliary inputs work too.

---

### Post by coverup1128 on 2006-12-29
I have the same question (ie, I want to convert VHS(VCR) to mpeg (DVD)). Using Windows (InterVideo DVD Creator) and my camcorder as an analog to digital interface device, I managed to copy some VHS tapes to DVDs hassle free. Unfortunately, tapes are quite old and the quality is not very good. Are there Linux tools which I could use to reduce noise while converting VHS to DVD? 

Also, each and every tutorial tells how convert VHS to DVDs using a capture card, but I use a camcorder which connects via FireWire. What tools can I use?

---

### Post by pseudonym on 2006-12-29
> **coverup1128 said:**
> I have the same question (ie, I want to convert VHS(VCR) to mpeg (DVD)). Using Windows (InterVideo DVD Creator) and my camcorder as an analog to digital interface device, I managed to copy some VHS tapes to DVDs hassle free. Unfortunately, tapes are quite old and the quality is not very good. Are there Linux tools which I could use to reduce noise while converting VHS to DVD? 

Also, each and every tutorial tells how convert VHS to DVDs using a capture card, but I use a camcorder which connects via FireWire. What tools can I use?
I think the tool you're looking for is [Kino]("http://www.kinodv.org/"), which can be had in the Ubuntu repositories.

As far as VHS > DVD goes, unsurprisingly, your results are highly dependant on how well the hardware is supported under Linux. For instance, I have a digital TV card with analogue inputs. The DTV side of it works fantastically in Linux, but the S-Video and Composite ports only produce rubbish, no matter what tools I use. So I had to resort to the card's windows-only recording software to do my VHS dubs (with, to be fair, quite good results).

A good place to check hardware support for this type of device (and I think video capture cards as well), is [Linux TV]("www.linuxtv.org"). For capturing tools, ffmpeg and mencoder are good choices, if a little intimidating at first.

---

### Post by coverup1128 on 2006-12-29
Thanks for the quick reply.

I do not have a video capture card or a TV video card. I have a camcorder which connects via FireWire. 

I was trying Kino before on Mandriva LE2005 a while ago. Unfortunately, it's interface  was not very intuitive - there were way too many options with very little explanation. As a result, the AVI I got had no sound and was of poor quality. The quality of the DVD was no better than I would get using InterVideo DVD Creator. What I am looking for is a possibility to reduce noise. If that is not possible, I'd rather stick with Windows.

You mentioned ffmpeg and mencoder, do they allow to capture from a camcorder? Unfortunately, I was unable to find a step by step (or line by line) tutorial on _how_ to use those tools _with a camcorder_. I believe the process should be quite standard, and therefore there must be some standard scripts or CLI commands to perform the task, but I could not find a set of such scripts. Every page I read describes a wealth of Linux possibilities instead of providing a concrete set of specific commands. The details are so scarce and incomplete that I began suspecting it's not possible to capture VHS under Linux at all :grin:

---

### Post by pseudonym on 2006-12-29
> **coverup1128 said:**
> I do not have a video capture card or a TV video card. I have a camcorder which connects via FireWire.
Sorry, the video capture card stuff was for the other person who was asking. I should have made that clear. Once you mentioned camcorder I thought 'Kino'. But...

> **coverup1128 said:**
>  I was trying Kino before on Mandriva LE2005 a while ago. Unfortunately, it's interface  was not very intuitive - there were way too many options with very little explanation. As a result, the AVI I got had no sound and was of poor quality. The quality of the DVD was no better than I would get using InterVideo DVD Creator. 
...that turns out to be not right for you.

> **coverup1128 said:**
> You mentioned ffmpeg and mencoder, do they allow to capture from a camcorder? Unfortunately, I was unable to find a step by step (or line by line) tutorial on _how_ to use those tools _with a camcorder_. I believe the process should be quite standard, and therefore there must be some standard scripts or CLI commands to perform the task, but I could not find a set of such scripts. Every page I read describes a wealth of Linux possibilities instead of providing a concrete set of specific commands. 
They are good tools, but to make them do what you want, you have to do a lot of swotting. This means eg. the mencoder  manpage and the mailing lists, both at the [MPlayer website]("http://www.mplayerhq.hu/"). If someone has distilled all this into a more manageable format, I haven't found it either.

BUT!...There are tools which may be more to your liking. I think with your input hardware, you will need dvgrab, which is the Firewire capture utility in Kino. You can install that separately via Synaptic or apt-get, and use it to capture to .avi . A good option then for an editing suite is [Avidemux]("http://avidemux.sourceforge.net/"), which has matured a lot in recent versions. It's got lots of filters, including denoise.

If that turns out to be not suitable either, you can check out the Linux forum at [Doom 9]("http://forum.doom9.org/forumdisplay.php?f=63"), which lists several possibilities for apps (should have included this link earlier :) ).

HTH :)

---

### Post by coverup1128 on 2006-12-29
Thanks. Doom9 seems to contain lots of useful stuff (at least it's all in one place :) ). Will give dvgrab+avidemux a go...

---

