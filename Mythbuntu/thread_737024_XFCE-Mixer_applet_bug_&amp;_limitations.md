---
title: "XFCE-Mixer applet bug &amp; limitations"
date: 2008-03-27
forum: Mythbuntu
---

### Post by pt123 on 2008-03-27
On Gutsy (alsa 1.0.14) my surround wasn't working but on Hardy (1.0.16) it did for a while .

The problem is caused by the limitations of XFCE-mixer which I assume is based on gnome-alsamixer

when I run these two they both show this errors
It keeps outputting this error msg:
* (gnome-alsamixer:13653): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Channel Mode"!

There are 2 options for channel mode- 2channel mode & 6 channel mode.
Each time I set it to 6 mode it goes back to 2.


I managed to get surround sound working by using a terminal and this command:
amixer set 'Channel Mode' 6ch

Interestingly Gnome's Volume applet knows how to handle these options. I am not sure what package to install to have that working in XFCE, if at all it will run.

I still can't understand why Mythbuntu uses XFCE and all its sub par features. How many new users of Mythtv, XFCE has turned away by showcasing a sub par MythTV system.

---

### Post by laga on 2008-03-27
Please file a bug report: [https://bugs.launchpad.net/ubuntu/+source/xfce4-mixer](https://bugs.launchpad.net/ubuntu/+source/xfce4-mixer)

> 
I still can't understand why Mythbuntu uses XFCE and all its sub par features. How many new users of Mythtv, XFCE has turned away by showcasing a sub par MythTV system.


Please click the link in my signature, then read the second item. Yes, the item about "complaining".

If you don't like it, just install gnome. Or don't install Mythbuntu. There are reasons Xfce4 is used. Nobody needs a full Gnome environment running behind their mythfrontend just because you found a bug in a beta release of Mythbuntu.

<rant>
I really wonder where this attitude comes from? Every time I look in this forum, the only thing I see is complaints. If you don't like it, you have a few options:
[list]
[*] Submit a patch
[*] Ask a question. **Politely**.
[*] Modify Mythbuntu to suit your needs. Either do it privately, or fork Mythbuntu and create your own flavour. If you want Gnome, just use it.
[*] Talk to the developers, make sane suggestions. Don't demand your changes to be implemented. Demanding architectural changes because of a bug in the volume control applet in Xfce is not a sane suggestion.
[/list]

But hey, maybe we can arrange a refund for your "sub par MythTV system"?
</rant>

---

### Post by foxbuntu on 2008-03-27
> **pt123 said:**
> I still can't understand why Mythbuntu uses XFCE and all its sub par features. How many new users of Mythtv, XFCE has turned away by showcasing a sub par MythTV system.

<big><rant>

As a developer for this project, a person spending numerous hours behind the scenes supporting the community and the code, This is sicking. People come into the forums and act like total asshats because they didn't get their favorite flavor of cheese. Well I have news for you, this is how the world works. We are doing the best for the most users. We have added support so there is no problems running a full Ubuntu Gnome desktop behind MythTV if you so chose. We chose Xfce because its slim and has less overhead while running MythTV. 

If you feel like replying to my message don't. This is a message from a fed up developer of people ranting like children over minute bugs instead of asking for help. If you had posted a message kindly asking for help, filed a bug with detailed problems, you would have received help. Now you get none.

</big></rant>

---

### Post by pt123 on 2008-03-27
Thanks for undeleting the post.

I will just like to state I am not free loading.
I am using my time to test a beta product and then report back any bugs.

It is counter-productive if I can not even comment on the frustrations of these bugs, by questioning why XFCE is being chosen ahead of Gnome. When Ubuntu has stated that it will end supporting for Xubuntu.

Don't get me wrong, I do appreciate the time effort you put into the distribution. 
That is why I don't like it being undermined by XFCE.

One of the reasons I like Ubuntu over the other OSes. Is the 6 month release cycle. We are able to get the latest updates in a well packaged and maintained distribution. My TV card wasn't supported well in Gutsy but in Hardy it is, similar story for my sound card.

This is why I don't know why you persist with XFCE when Gnome is developed at a much faster rate than XFCE. 

The problem with enabling the surround sound was because XFCE volume applet couldn't handle these input choices from Alsa, but Gnome had this covered a few distributions ago. 

You can't expect new linux users which Ubuntu has targeted to start using command line to get surround sound to work. Especially when you (Mythbuntu) have put great effort into getting MythTV to work out of the box.

I do not know how or when you guys decide which desktop environment to use, but you seriously need to reconsider it.

---

