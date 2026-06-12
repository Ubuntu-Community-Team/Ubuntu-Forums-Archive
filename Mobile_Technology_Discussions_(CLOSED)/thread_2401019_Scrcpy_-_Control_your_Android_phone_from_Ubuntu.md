---
title: "Scrcpy - Control your Android phone from Ubuntu"
date: 2018-09-12
forum: Mobile Technology Discussions (CLOSED)
---

### Post by ulsterfc on 2018-09-12
Hi guys,
            I use a program called scrcpy on Windows to remotely control my android phone. I was trying to find a deb for it but couldn't so I made one based on the rpm and it worked ok on my computer after moving one file. So now I can control my Android device directly from Ubuntu, as long as it's plugged into the usb.

If anyone's interested in helping me test this then please check the instructions here.  I want to improve the quality of the deb or even look at some way to get a ppa or something going. I think this could be really good for some people and maybe could in some way be better inegrated into Ubuntu.

The original source is on github at: [https://github.com/Genymobile/scrcpy](https://github.com/Genymobile/scrcpy) and there is an issue relating to debs at: [https://github.com/Genymobile/scrcpy/issues/256](https://github.com/Genymobile/scrcpy/issues/256)


I've made a package based on that allows your to easily install it. [http://johnmccourt.com/files/scrcpy_1.3~git20180820-2.2_amd64.deb](http://johnmccourt.com/files/scrcpy_1.3~git20180820-2.2_amd64.deb)

[LIST=1]
[*]Download and Install this deb installer using your favourite package manager
[*]Start scrcpy in terminal by typing scrcpy
[*]If it tells you it can't find the server jar then you should be able to find it in /usr/share/scrcpy and put it into the correct location. You may need to use sudo to write to the necessary folders.
[/LIST]
If you cannot find that server jar  file then I've kindly provided a download which you can copy to the necessary location:
[http://johnmccourt.com/files/scrcpy-server.jar](http://johnmccourt.com/files/scrcpy-server.jar)
 
On your device itself you will need to have the following enabled:

[LIST]
[*]Developer mode enabled
[*]usb debugging
[*]Simulate input.
[/LIST]
Simulate input is necessary if you want your mouse clicks to actually work on the device.
Any questions throw me a comment.

I don't have a site yet for this fork/package, but some details are available on my blog. I'm thinking that Github might be a good place to host the project from, or we can work more with the original developer of the app to make sure there is an Ubuntu package on his github site. Hopefully with some of the information I have provided the Ubuntu community can at least be informed and work together on getting this included on a proper level.
 
[https://xn--joh-9ma.com/control-your-android-device-in-ubuntu-with-scrcpy/](https://xn--joh-9ma.com/control-your-android-device-in-ubuntu-with-scrcpy/)

[IMG]https://johñ.com/wp-content/uploads/2018/09/scr-149x300.png[/IMG]

---

### Post by QIII on 2018-09-12
Hello!

Normally a link in a "first time post" gets our attention, as yours did.  That is often a sign of spam.  But I looked with a less jaundiced eye on this thread.  I perceive no intention for personal gain.

From the [Ubuntu Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules"):

> Links: You may post links to sites with content that is acceptable according to this code of conduct. This is most useful when giving tech support and explaining a topic and then linking to a wiki page or Linux site with more information. You may also link to your personal site. 

We also frown on gratuitous self-promotion.

Your site does not seem to be overtly commercial (in your own interest) and I don't see a "donate" button, which we would consider to be commercial and in the financial interest of the user.  This seems to be an item that could be of interest to the Ubuntu community, so I will allow it pending discussion among the Staff.  We do allow links to commercial sites, like Phoronix, when the content is applicable by way of instruction and there is no personal benefit to the user in linking it.  That is, don't link to a site from which you profit personally.

Please, however, link your blog only when it is appropriate for the benefit of the community.  I have in the past linked my own blog articles when they are good tools for explaining or solving issues.  A link to my blog is also in my signature.  

This being a discussion forum, your post also seems appropriate.  But ***do*** please put the instructions for testing here, and please keep the discussion here so that the entire community has the opportunity to benefit from it.  Taking the discussion away from here robs the forum community of any benefit. *** I would also ask you to post the source code (git, say) and provide a link to it before you post the instructions so that it can be inspected by the community.***

Don't do blog links habitually without there being some benefit to everyone, though.

Cheers!

---

### Post by ulsterfc on 2018-09-12
Thanks. That sounds fair enough. I'll update the orginal post with the instructions. Hard to know how to go about talking about these things sometimes.

---

### Post by QIII on 2018-09-12
I've updated my original post, too, so please read again.

Cheers!

---

### Post by 00110011readf on 2018-10-13
Hi, the .deb is already installed but when I type scrcpy this message come out "[FONT=monospace][COLOR=#000000]scrcpy: error while loading shared libraries: libavformat.so.58: cannot open shared object file: [/COLOR]
No such file or directory" what should I do?

[/FONT]

---

### Post by d9k-m on 2018-10-26
@ulsterfc, thanks for your work but download link is broken

---

### Post by Mrhihat on 2019-03-04
I am getting this 
"[FONT=monospace][COLOR=#000000]error while loading shared libraries: libavformat.so.58: cannot open shared object file: [/COLOR]
No such file or directory" [/FONT]too.

I have been looking for a decent install guide for scrcpy for quite some time now. 
I have heard that it also is possible to get it working over wifi?

Any assistance would be greatly appreciated

---

### Post by sisco311 on 2019-06-12
> **Mrhihat said:**
> I am getting this 
"[FONT=monospace][COLOR=#000000]error while loading shared libraries: libavformat.so.58: cannot open shared object file: [/COLOR]
No such file or directory" [/FONT]too.

I have been looking for a decent install guide for scrcpy for quite some time now. 
I have heard that it also is possible to get it working over wifi?

Any assistance would be greatly appreciated

You can install it as a snap:   [https://snapcraft.io/scrcpy](https://snapcraft.io/scrcpy)

If you prefer to build it from source then please follow the instructions at: [https://github.com/Genymobile/scrcpy/blob/master/BUILD.md](https://github.com/Genymobile/scrcpy/blob/master/BUILD.md)

If you run into any issues, please start a new thread.

---

### Post by SeijiSensei on 2019-06-12
I just use KDEConnect.

---

