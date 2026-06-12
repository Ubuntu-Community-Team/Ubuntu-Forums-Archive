---
title: "More DVD questions"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by brightmatter on 2006-10-26
Yes, I know, there are a million people asking a million questions regarding their DVD ROMs but I am 2 days new into Ubuntu and all I ever needed was for it to access the internet, use ooffice and play DVDs.  2 out of three are good to go.  Now for the third.

Movie Player states it cannot play my DVD.  It is a normal DVD, nothing special.  I read the page regarding restricted files and it said I need some kind of codec package.  It did not however tell me the following.

1.  What is the website address for the codec package install (the link)?
2.  once downloaded, where do i put it (what folder)?
3.  Once it is in the folder, what is the command line i type to install it?

it is telling me stuff like i need to enable restricted files in system>administration>synaptic package manager>settings>repository and then select every check mark and then enter each selection and select universe and multiverse.  I do this and then close.  I reenter to check to make sure the settings worked and they are again unchecked.  I check them again and again leave.  I reopen them again to check to see if it is still checked and they are again unchecked.](*,) 

What does any of that stuff got to do with my DVD not playing and where is the codec?:confused: I am so confused, please, someone help me.:(

I found these commands that are supposed to work.  I open terminal and paste them in and press enter...... all i get is an error.  Next I try one line at a time..... again, error.

sudo apt-get install libdvdread3
(E: Couldn't find package libdvdread3)

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

(sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found)

sudo apt-get install totem-xine

---

### Post by vkellers on 2006-10-27
brightmatter,

I think that the "Couldn't find package..." messages are popping up because the Universe / Multiverse repositories are not enabled, as you mentioned in our message.

You may want to try to enable them following the instructions detailed in this page: [https://help.ubuntu.com/community/Repositories/Ubuntu#what]("https://help.ubuntu.com/community/Repositories/Ubuntu#what")

Once that is done, you should be able to install the CSS. You may want to follow the instructions detailed in this page to install CSS: [https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")

HTH

---

