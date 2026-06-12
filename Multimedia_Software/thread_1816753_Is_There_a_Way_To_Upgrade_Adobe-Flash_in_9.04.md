---
title: "Is There a Way To Upgrade Adobe-Flash in 9.04?"
date: 2011-08-02
forum: Multimedia Software
---

### Post by Sky Aisling on 2011-08-02
Hello,

I am running **Jaunty Jackelope 9.04** on a **Compaq Presario 2100 with 512 RAM.** Browser is **Firefox 3.0.8.**
Jaunty runs well on this old machine.
But, it needs **Adobe-Flash** upgraded in order to see and hear videos on for example: YouTube.

Is there a way to upgrade **Adobe-Flash** in **9.04**?

I've searched the repositories and can't seem to find a solution there.

Thank you in advance for any suggestion or guidance you may offer.

---

### Post by beew on 2011-08-02
The repository is closed down because 9.04 has reached end of life and is no longer supported. You should do a fresh install of a newer version of Ubuntu. For an old machine like yours I would recommend  Xubuntu/Lubuntu 10.04, which ran well on my 8 year old Ispiron 8500 with512Mb of ram.

Also your Firefox is no longer supported as well, and it is a security risk to go online with it.

---

### Post by Sky Aisling on 2011-08-02
Thank you **beew** for your timely reply.

I've tried Xubuntu 10.04 with negative results.
I'll give Lubuntu 10.04 a try.
I'll edit this posting results then mark thread closed.

**Edit:**
Tried Lubuntu via Live CD.  Looked like maybe it would go, so, I installed it.
Unfortunately, Lubuntu 10.04 performed as poorly as Xubuntu 10.04 on this machine.  
Lubuntu move at a snail's pace.  Mouse was barely controllable. 
Xubuntu 10.04 was not even controllable via mouse or glide pad and simply froze.

Too bad about Jaunty Jackelope 9.04, it runs well on the machine.

Your quick response was appreciated.

---

### Post by lovinglinux on 2011-08-03
> **Sky Aisling said:**
> Thank you **beew** for your timely reply.

I've tried Xubuntu 10.04 with negative results.
I'll give Lubuntu 10.04 a try.
I'll edit this posting results then mark thread closed.

**Edit:**
Tried Lubuntu via Live CD.  Looked like maybe it would go, so, I installed it.
Unfortunately, Lubuntu 10.04 performed as poorly as Xubuntu 10.04 on this machine.  
Lubuntu move at a snail's pace.  Mouse was barely controllable. 
Xubuntu 10.04 was not even controllable via mouse or glide pad and simply froze.

Too bad about Jaunty Jackelope 9.04, it runs well on the machine.

Your quick response was appreciated.

I am not sure if it will work, but you can try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). It will install the latest Flash 11 Beta. However, since your machine is already struggling, it probably will have difficulties running flash videos, since Flash uses a LOT of resources. You could try [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/versions/") with gecko-mediaplayer. Make sure to get version 2.1.14, which works with YouTube again. This add-on allows to watch YouTube, Vimeo and Metacafe videos using a better plugin or an external player, which can reduce CPU usage considerably.

I am the developer of both add-ons, so feel free to ask any questions.

---

### Post by Sky Aisling on 2011-08-03
**lovinglinux** wrote:

> I am not sure if it will work, but you can try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/").  It will install the latest Flash 11 Beta. However, since your machine  is already struggling, it probably will have difficulties running flash  videos, since Flash uses a LOT of resources. You could try [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/versions/")  with gecko-mediaplayer. Make sure to get version 2.1.14, which works  with YouTube again. This add-on allows to watch YouTube, Vimeo and  Metacafe videos using a better plugin or an external player, which can  reduce CPU usage considerably.

I am the developer of both add-ons, so feel free to ask any questions.     Thank you lovinglinux,  I intend to explore your suggestion and post results in a few days.

I was hoping someone would give a suggestion to keep Jaunty Jackelope going a while longer.
Jaunty is such a good distro, particularly for beginners.  Also, I've found that Jaunty 9.04 runs well on the older machines.   (The machine I am fixing up is for a newbie.  I get these old laptop machines and install either Xubuntu or Puppy distros in them, then give them to low-come people who need a computer for simple communication, like email and web-surfing.  Also, this little effort may delay the machine from going into the trash heap of e-waste a while longer.)

There is also the issue of Mozilla Firefox 3.0.x having a security bug?

I'll tinker and post again later.

---

### Post by lovinglinux on 2011-08-03
> **Sky Aisling said:**
> **lovinglinux** wrote:

Thank you lovinglinux,  I intend to explore your suggestion and post results in a few days.

I was hoping someone would give a suggestion to keep Jaunty Jackelope going a while longer.
Jaunty is such a good distro, particularly for beginners.  Also, I've found that Jaunty 9.04 runs well on the older machines.   (The machine I am fixing up is for a newbie.  I get these old laptop machines and install either Xubuntu or Puppy distros in them, then give them to low-come people who need a computer for simple communication, like email and web-surfing.  Also, this little effort may delay the machine from going into the trash heap of e-waste a while longer.)

There is also the issue of Mozilla Firefox 3.0.x having a security bug?

I'll tinker and post again later.

As already mentioned, your Ubuntu and Firefox versions are old and unsupported. I don't have any reference right now, but there will certainly be security issues, since Firefox 3 hasn't been updated for more than a year. After FF 3.0, there was FF 3.5.0 through 3.5.19, FF 3.6.0 through 3.6.19, FF 4 and FF 5. FF 6 will be released in two weeks. So, lots of versions and security patches. Your version is really old.

At least you should try to get Firefox 5 running on your machine. You can download it from Mozilla and install manually. See [http://www.webgapps.org/tutorials/firefox/general/installing-other-versions](http://www.webgapps.org/tutorials/firefox/general/installing-other-versions)

You will see a huge improvement in performance. Check the performance difference on Peacekeeper benchmark:

[[IMG]http://www1.picturepush.com/photo/a/6233469/640/6233469.png[/IMG]](http://picturepush.com/public/6233469)

---

