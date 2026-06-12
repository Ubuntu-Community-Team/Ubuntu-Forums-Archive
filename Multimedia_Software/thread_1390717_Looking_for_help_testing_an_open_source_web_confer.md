---
title: "Looking for help testing an open source web conferencing system: BigBlueButton"
date: 2010-01-25
forum: Multimedia Software
---

### Post by ffdixon on 2010-01-25
Hi Everyone,

We've been hard at work building an open source web conferencing system called BigBlueButton.  It's far enough along that we're comfortable sharing it with broader audience to get more help testing it.

The project is hosted at Google Code.  

BigBlueButton offers real-time sharing of slides, voice, chat, video, and desktop sharing (yes, desktop sharing on Linux). 

If you are interested to try it out, help find bugs, give us feedback, and, if you want, help contribute to the project, here are some links:

You can download a BigBlueButton Virtual Machine (its running Ubuntu 9.04): 
   [http://code.google.com/p/bigbluebutton/wiki/BigBlueButtonVM](http://code.google.com/p/bigbluebutton/wiki/BigBlueButtonVM) 

You can install BigBlueButton on any Ubuntu 9.04 32-bit (server or desktop) with apt-get using five commands: 
   [http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu](http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu) 


We're creating BigBlueButton for University or Colleges to help them offer a high-quality learning experience to remote students.  Feedback welcome.

Regards,... Fred

---

### Post by darkwave on 2010-01-28
We, at [_http://mondonerd.com_](_http://mondonerd.com_), are testing both the VM and 5 commands Ubuntu installation... I share here our experiments ;)

The whole experience was very interesting and **I suggest to every student/professor listening to spend some time installing BBB in their intranet and play** with webcams, voice chat and sharing funny pdfs, ppts and other formats! ;-)

**Ubuntu 9.04**

On a quadcore we installed BBB using _[the handy 5 commands instructions]("http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu")_. Everything goes well and we could start conference in a few minutes! Very exciting!!! :popcorn:

We only had a problem when a user upload a file: firefox seems to hung and if the user interrupt the upload killing firefox BBB go on working but doesn't allow any more users to login :-(

Other notes about the client interface:

 * On Netbooks (like Asus eeePC) the BBB dashboard results to be too big. Using fullscreen mode resolve the issue but you cannot use the chat cause it's disabled.
 * Some error with webcams windows size
 * If you close some windows then is not possible to resume them... or are we missing some icon? :-)
 * Please document how to quit the music and girl voice in the voice chat... She sounds like a real user listening music and scares :-D

**With QEMU**

The VM was tested using QEMU converting the vmWare image you provided.

QEMU need to run using [_TAP interface_]("http://www.qemu.org/qemu-doc.html#SEC29") (using redirection of port 80 instead of TAP shows only an nginx welcome page)

We were able to see the BigBlueButton homepage but... we couldn't create a conference! :-(

**[SIZE="3"]We stay tuned, keep on BBB Team![/SIZE]**

ciao,
dw

---

### Post by ffdixon on 2010-01-30
Hi Darkwave,

Thanks for your feedback!

We're targeting the educational market with BigBlueButton and we welcome any suggestions for improvements.

> We only had a problem when a user upload a file: firefox seems to hung and if the user interrupt the upload killing firefox BBB go on working but doesn't allow any more users to login.

We've noticed some problems on firefox and are tracking them it this issue:

   [http://code.google.com/p/bigbluebutton/issues/detail?id=198](http://code.google.com/p/bigbluebutton/issues/detail?id=198)

> On Netbooks (like Asus eeePC) the BBB dashboard results to be too big.

We agree.  At some point we're going to build some more intelligence into the auto-arrange button to lay out the windows on a smaller screen.

> Some error with webcams windows size

The webcam windows are fixed size.  If you are watching the webcams from five participants (and there is no restriction ... you could watch ten webcams if you wish), they do take up space.

We've thought about creating a single window with a tile of all other webcam windows.  This would take up less space, and opens the door for more intelligence in handling the streams, such as making the current person larger.

> If you close some windows then is not possible to resume them... or are we missing some icon?

That's correct.  You'll notice we've removed the 'x' button on some of the windows to make it harder for a person to accidentally close them; however, if you right-click and close, you can close them.

There's a whole area for window management that can be incrementally improved over iterations.  The challenge is to do this without complicating the interface.  One thought is to enhance the reset layout button to restore any windows that were closed.

> Please document how to quit the music and girl voice in the voice chat... She sounds like a real user listening music and scares

We'll look at adding it to the FAQ :-).


> We were able to see the BigBlueButton homepage but... we couldn't create a conference!

First thing you can do is type

  bbb-conf --check

This will look for common problems that may prevent BigBlueButton from loading.

If it gives you any warnings, please post them to this thread and we'll see if we can't get you up and running.

Regards,... Fred

---

