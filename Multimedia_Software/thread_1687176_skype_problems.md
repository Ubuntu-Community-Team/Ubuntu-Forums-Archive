---
title: "skype problems"
date: 2011-02-13
forum: Multimedia Software
---

### Post by chw1984 on 2011-02-13
Hello everybody,

I have tried to install skype through the ubuntu software center. This gave an error message (cp. further down). I can still start Skype and log in with my username. All my contacts stay grayed out even though I am quite sure that somebody should be online. When trying to call the test call service is seems to work at first but then after a while the call is canceled.

My feeling is that my skype installation does not get access to the internet. Maybe I should use a different port? Right now 23399 is chosen... I tried to change it to 81 as suggested in the wiki. This did not work and the port number stayed as it was.

I also tried to delete the directory ~/.Skype as suggested in many threads... However this did only reset my preferences and did not solve the problem in my case.

I am running Ubuntu Netbook Remix (10.04) on an Acer Aspire One. The Skype version is 2.1.0.81.

I would appreciate any help...


Thanks in advance, Chris


P.S. Here the error message when installing Skype:

%%%%
installArchives() failed: Selecting previously deselected package libaudio2.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 230164 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9.2-3_i386.deb) ...
Selecting previously deselected package libmng1.
Unpacking libmng1 (from .../libmng1_1.0.9-1ubuntu1_i386.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.6.2-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.6.2-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.6.2-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4%3a4.6.2-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.6.2-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package skype.
Unpacking skype (from .../skype_2.1.0.81-1ubuntu5_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up libaudio2 (1.9.2-3) ...

Setting up libmng1 (1.0.9-1ubuntu1) ...

Setting up libqtcore4 (4:4.6.2-0ubuntu5.1) ...

Setting up libqt4-xml (4:4.6.2-0ubuntu5.1) ...

Setting up libqt4-dbus (4:4.6.2-0ubuntu5.1) ...

Setting up libqt4-network (4:4.6.2-0ubuntu5.1) ...

Setting up libqtgui4 (4:4.6.2-0ubuntu5.1) ...

Setting up skype (2.1.0.81-1ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
%%%

---

### Post by chw1984 on 2011-02-14
I turned on Skype this morning and it was working. I don't have a clue what I did to make it work...

However when I restarted it I needed to play around a bit (make a few calls to the call testing service, which failed) and after that things were working again... So my issue does not seem to be fully resolved but at least it seems that with some patience I can actually use Skype.


If anybody has further ideas what the problem could be please tell me but for now I will mark the thread as solved.



Thanks, Chris

---

