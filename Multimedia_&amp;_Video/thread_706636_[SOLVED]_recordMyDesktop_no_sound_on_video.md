---
title: "[SOLVED] recordMyDesktop no sound on video"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by philidox on 2008-02-24
I'm trying to get recordMyDesktop to record audio from my microphone.  I have skype installed on my computer and I can talk to people via microphone no problem and I can speak into my microphone and hear myself thru the speakers so I can safely rule out that the microphone is working.  Anyone know how to configure recordMyDesktop to record from microphone or setup this jack server?

---

### Post by philidox on 2008-02-25
FIX IT!!!

This video explains it all [http://www.youtube.com/watch?v=T-tyN2EbYNs](http://www.youtube.com/watch?v=T-tyN2EbYNs). Please whether this fix your issue or not come back and post here.  I need to know if it works or if my youtube video needs tweaking.  Give thanx, critics, or something.  Enjoy

---

### Post by Locutus_of_Borg on 2008-02-25
[http://recordmydesktop.iovar.org/rug/p1_2c.php](http://recordmydesktop.iovar.org/rug/p1_2c.php)


alternatively, you can record two separate streams, audio/video and merge them with ogmmerge which you can get with "sudo apt-get install ogmtools"

---

### Post by dolphinsonar on 2008-03-04
> **philidox said:**
> FIX IT!!!

This video explains it all [http://www.youtube.com/watch?v=T-tyN2EbYNs](http://www.youtube.com/watch?v=T-tyN2EbYNs). Please whether this fix your issue or not come back and post here.  I need to know if it works or if my youtube video needs tweaking.  Give thanx, critics, or something.  Enjoy


Thanks, that video was very helpful!

---

### Post by kkaland on 2008-05-08
Worked for me, thanks dude! Linux is humbling and definitely helps me train my time management, heh, if you know what I mean.

---

### Post by greglaun on 2008-05-16
philidox, thanks for your solution!  Since you ask for feedback on the youtube site, I should note the following:

(1) Your solution involves installing closed-source software, and software that a court has ruled violates the GPL.  Getting sound card information does not require you do such a thing, and many Linux users simply aren't going to install Skype to fix this problem. Plus you're asking people to take up skype user names that they're not going to use!  That's just unfair to people who actually want those skype user names.

(2) It makes no sense to post a youtube video for this.  This is especially the case since flash doesn't work properly on 64-bit computers (which many Linux users have).  Your solution could be written out in a few lines of text.  Posting the video makes it seem like you're trying to inflate the number of views on the video rather than trying to help people.  I know that's not the case, but some people might think that.

I would suggest either responding to a bug report explaining how this might be fixed and then linking people to the bug report, or simply pasting a few lines of commands that can be copied into a terminal.

In most cases your sound card is just going to be hw:0 if you only have one sound card.  If you have more than one, you might as well install qjackctl and use jack for recordmydesktop.

---

### Post by philidox on 2008-05-16
> **greglaun said:**
> philidox, thanks for your solution!  Since you ask for feedback on the youtube site, I should note the following:

(1) Your solution involves installing closed-source software, and software that a court has ruled violates the GPL.  Getting sound card information does not require you do such a thing, and many Linux users simply aren't going to install Skype to fix this problem. Plus you're asking people to take up skype user names that they're not going to use!  That's just unfair to people who actually want those skype user names.

(2) It makes no sense to post a youtube video for this.  This is especially the case since flash doesn't work properly on 64-bit computers (which many Linux users have).  Your solution could be written out in a few lines of text.  Posting the video makes it seem like you're trying to inflate the number of views on the video rather than trying to help people.  I know that's not the case, but some people might think that.

I would suggest either responding to a bug report explaining how this might be fixed and then linking people to the bug report, or simply pasting a few lines of commands that can be copied into a terminal.

In most cases your sound card is just going to be hw:0 if you only have one sound card.  If you have more than one, you might as well install qjackctl and use jack for recordmydesktop.

we'll that was very informative but murphy's law states "if it works but stupid, than it aint stupid".  I think skype would love me for promoting their product and usernames are a dime a dozen. I appreticate your comments but was hoping from more of a technical aspect than legal.  Someone suggested to use zoom which was a great idea. if you know how to get the technical data provided by skype without installing that would be great!

---

