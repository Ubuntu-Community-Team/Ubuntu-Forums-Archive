---
title: "Edit AVI &amp; Add MP3"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by inclininwirefree on 2007-06-11
;)

I have just presented myself a fresh installation of Ubuntu Studio and would like to commence a video editing job at hand.

Presently, the system can't even play an .avi.

- What are my options for editing softwares?
- What formats, encoders/decoders are required?

I understand I can't get started out-of-the-box :(


Would appreciate sound advise.

Best,
inclininwirefree

---

### Post by scott_g on 2007-06-11
> **inclininwirefree said:**
> 
Would appreciate sound advise. -- Is that a pun?

The first time you try to play a restricted format, it should ask to install the correct codecs.

There are a few good video editors (I'm not sure which ones are included in the Ubuntu Studio):

Avidemux (good for converting between video formats)
Kino (good for capturing and limited editing)
Cinelerra (excellent for editing; similar in layout to Premier)

Audacity (audio editing/converting)

All of these are available in the repositories except for cinelerra; its repositories are:

```

- i686:
    deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./
- athlonxp:
    deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/ ./
- pentium4:
    deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/ ./

``` (from [http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README))

Hope it helps,
Scott G.

---

### Post by inclininwirefree on 2007-06-13
You've been an enormous help, scott_g!

(man!! why is it so hard to install an app in linux, per se?!?)

I am thru w/ installing Cinelerra. Could you please explain what 'repositories' are and how I can get Avidemux.

Thx!

---

### Post by scott_g on 2007-06-13
Sure thing.

Repositories make your life easier.  They store a lot of programs and applications on servers.  These repositories are easy to interact with, using software that comes with your Ubuntu installation.  The easiest example of this is the "Add/Remove Software" application on the Applications menu.  Enter in an application in the search field, check it, and click apply, and it is installed.  To install Avidemux, type avidemux into the search box in the Add/Remove Software tool, check its entry off, and click apply.  (I believe msot of the other programs I previously mentioned can be installed this way; if they aren't found, try the Synaptic Package manager, which is explained below).

I actually find this process easier than on Windows.  The Add/Remove Software tool only searches the default repositories given by the Ubuntu team; some software (like Cinelerra) are not in these repositories, yet have their own.  

To add a repository (to install Cinelerra; highly recommend it), go to System>Administration>Software Sources, and click on 3rd Party Software.  Then, click add, copy and paste the line that corresponds to your version of Ubuntu from above (likely "deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./"), and click OK.  Close the dialog box, then go to the Synaptic Package Manager (I'm using this one as it shows more packages; ignore all the ones with funny names like lib etc; they are dependencies that will automatically be installed); to get to the Synaptic Package Manager, go to System>Administration> Synaptic Package Manager, then do a search for Cinelerra (it may ask to install some extra packages; this is OK).  Click apply and wait for it to download the software and install it.  

Either way, the new software should be entered into the menu under Applications>Sound and Video.

Hope it helps; was confusing for me too; I used to try to hunt down all the dependencies myself, makes you appreciate package managers :D.

Scott G.

---

