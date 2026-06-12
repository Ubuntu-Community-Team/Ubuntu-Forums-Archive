---
title: "I want multiple lirc receivers"
date: 2010-09-19
forum: Mythbuntu
---

### Post by forkd on 2010-09-19
I have a nice myth machine with the snapstream RF remote working great.  But I have some little tweaks I'd like to do to improve my box like adding another IR receiver.

I'd like to add an IR Receiver in order to be able to use other remotes and perhaps even use the IR remote that came with the TV.  I don't know how to add another instance of lirc for receiving although there is plenty of information out there regarding multiple transmissions.  

Any direction is appreciated.

I'm moderately competent with writing and editing lirc scripts as I've always fleshed out my own and in the early years (my first build was on Red Hat >7 <Fedora) I've even compiled and configured lirc from scratch.  Not that I remember exactly how to do it but I am capable of figuring it out :)

I also have an extra machine for testing purposes so I'm not too concerned with trying stuff that may mess up my box.

---

### Post by EricDP on 2010-09-20
You only need one receiver to receive from several remotes. Just append all the lircd.conf files into a single file.

---

### Post by ayourk on 2011-07-28
I have 3 remote receivers, one is a Microsoft MCE USB, one is an ATI X10, and the third is a Hauppauge.  I'd like to get all of these working.  I intend to use the ATI remote as a remote mouse and the others as remotes for VLC and Hulu.

I did find [**this link**]("http://www.mythtv.org/wiki/MultiLIRC") that talks about Multiple LIRC instances, but apparently it was written before upstart.  If anyone has something similar already I'd like to get it, otherwise I'll convert the natty /etc/init.d/lirc to behave something like this.

For the remote mouse aspect, I already found the necessary xorg.conf config adjustments.

---

### Post by thatguruguy on 2011-07-28
If you launch Hulu from the myth menu, you don't need a separate remote.  Just set up Hulu to recognize the remote you usually use.  I think I put up a tutorial on how to switch back-and-forth on here some time ago; if not, I'd be happy to provide some instruction.

Are you running vlc because there are videos that can't be handled from mythvideo, or is there some other reason?

---

### Post by pils92 on 2011-12-18
Alright I don't know the O.P.'s setup but I have two monitors mirrored in seperate rooms. I want a IR receiver in each room so two receivers are neccessary. please help with any ideas how to make this function. They are both mceusb remotes and receivers. Both receivers made by formosa industrial computing but not the same models. Any help would be appreciated.

---

