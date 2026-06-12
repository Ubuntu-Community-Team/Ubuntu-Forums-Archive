---
title: "How to control rhythmbox with ssh"
date: 2010-08-20
forum: Multimedia Software
---

### Post by Tachyon60 on 2010-08-20
I was looking around for a way to control rhythmbox playback on a remote computer with ssh (or telnet) and found a few archived posts asking about this without a working answer.

After a little searching I found a way to do this on [commandelinefu]("http://www.commandlinefu.com/commands/view/4599/remote-control-for-rhythmbox-on-an-ubuntu-media-pc"): after you ssh into the computer use the following command to alias 'rc' as a command to control the current rhythmbox session

```
alias rc='env DISPLAY=:0.0 rhythmbox-client --no-start'
```

Now you can use any of the rhythmbox-client controls in a ssh session with ease!
Some useful commands are:
rc --play
rc --pause
rc--volume-up
rc --mute
the full list of commands can be found [here]("http://www.linuxcertif.com/man/1/rhythmbox-client/")

Optionally, you can also alias the rc command to include the ssh login such as
```
alias rc='ssh ${MEDIAPCHOSTNAME} env DISPLAY=:0.0 rhythmbox-client --no-start'
```

Hope this helps someone

---

### Post by sideaway on 2010-09-02
Helped me heaps, cheers mate! :)

---

### Post by v1ad on 2010-09-02
bookmarked, tx always wanted to do this.

---

### Post by mjuchli on 2010-09-15
Bookmarked too. I think it will help me when I get home and try it.

Thanks!

---

