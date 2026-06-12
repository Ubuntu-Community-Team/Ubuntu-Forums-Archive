---
title: "gstreamer-bad is good. gs-good is bad"
date: 2010-03-04
forum: Multimedia Software
---

### Post by degarb on 2010-03-04
On streamick.com  it auto installed gstreamer-good  which did not do all the streams.  I later tried after a few weeks of frustration replacing it with gstreamer-bad. Now all the streams work.  (sometimes I am forced to open with movie player, but at least they always play.)

It seems not good that the auto installing plugin and logical name, doesn't work.  But something labeled bad, works.

---

### Post by wojox on 2010-03-04
gstreamer-ugly works to. Good, Bad, and Ugly

---

### Post by degarb on 2010-03-04
> **wojox said:**
> gstreamer-ugly works to. Good, Bad, and Ugly


I haven't tried it.  Is it worth installing if I have bad; any better than bad?

---

### Post by wojox on 2010-03-04
Sure is. ;)

---

### Post by degarb on 2010-03-04
> **wojox said:**
> Sure is. ;)


I assume I just install it.  no uninstalling any of the older gstreamer?

What do you think is better about it?

And just to confirm,  is everything playing for you on streamick.com with gstreamer-ugly as your choice?  (I just googled it, and am apprehensive, since they claim the gstreamer-good codecs are functional, but they are not. And they claim the ugly are functional too, unlike the bad.  Since ubuntu has no rollback, I don't want to risk breaking gstream permanently if un-installing ugly doesn't bring back functionality, if it breaks something. )

---

### Post by degarb on 2010-03-04
I just checked in synaptic,  looks like ugly is installed here, when bad installed.

What is elisa  I would like a pvr, if it would record small files on external usb drive.

---

### Post by Seq on 2010-03-04
The Gstreamer site has a description of the [split plugin packages]("http://gstreamer.freedesktop.org/documentation/splitup.html"). Scroll down to the section called "The Lowdown".

Basically:
[LIST]
[*]"Good" are well developed, proper plugins licensed as LGPL. 
[*]"Ugly" are also well developed, proper plugins, but they may cause legal issues to distribute due to either licensing or scary patent worries.
[*]"Bad" are plugins that are either not ready for prime-time, or have not received enough testing to be considered as such. If they were cleaned up and approved, they would become either Good or Ugly.
[/LIST]

---

### Post by wojox on 2010-03-04
> **degarb said:**
> 
What is elisa  I would like a pvr, if it would record small files on external usb drive.

No idea about elisa. seq posted a good definition on the three. I've got all three installed and don't have and conflicting dependencies. (Knock on wood).

---

### Post by 00czar00 on 2011-03-15
If I install ugly or bad, does it replace good??? It says something of the sort under the dependencies menu in properties tab of Synaptic...

---

### Post by wkulecz on 2011-03-15
The Gstreamer setup is horribly complex, but if you stick with the repo versions and trust the dependencies, you can install all but a few (mostly the fluendo ones) without conflicts as needed.

---

