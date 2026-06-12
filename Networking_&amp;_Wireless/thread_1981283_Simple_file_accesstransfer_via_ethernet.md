---
title: "Simple file access/transfer via ethernet?"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by doubi on 2012-05-16
Hi all,

I want to rsync a large amount of data between two laptops, one running Ubuntu 10.04, one running 12.04.

When they're each connected to the house wireless they can always see each other on the network, either just by going to "Network" in Nautilus or drilling down to Network > Windows Network > WORKGROUP. I can access my Samba shares on each laptop fine this way, but it's very slow, so I'd like to do the same via ethernet.

I've followed [this thread]("http://ubuntuforums.org/showthread.php?t=1126718&page=2") and gotten to the stage where each can ping the other, but they don't show up as Windows shares. I got no further by following [this other thread]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=1031300"), in which the OP ended up installing openssh-server. Surely if both machines are demonstrably set up correctly with Samba (since I can navigate to each other machine fine when connected with wireless) I shouldn't have to resort to that?

I also followed [this LinuxQuestions thread]("http://www.linuxquestions.org/questions/linux-networking-3/file-transfer-using-ethernet-cross-over-cable-802756/"), which again got me able to ping, but when I go to Network in Nautilus they can't see each other. [Yet another thread]("http://ubuntuforums.org/showthread.php?t=1753070") got me no further. Just trying to say I *have* tried to look around and follow instructions on this but something's not quite right!

By all accounts, one they're able to mutually ping their Samba shares should just work. That's not happening. I've not set up any special firewall or anything on either machine. Ideas much appreciated!

---

### Post by papibe on 2012-05-16
Hi doubi.

If you install openssh-server in just one of the machines, you would easily rsync to and from it.

First install the package:
```
sudo apt-get install openssh-server
```
Then rsync:
```
rsync -avx source/ user@othermachine:destination/
```
That is what I use to rsync between my machines.

I hope that help, and tell us how it goes.
Regards.

BTW: Ii would be much better to do the transfer of large amount of data using a **wired** connection. It could be an enormous difference in the time needed for the transfer.

---

### Post by doubi on 2012-05-19
Hi papibe,

Thanks for your suggestion. I was indeed going for a wired transfer, via ethernet.

On your recommendation I tried installing openssh-server again (I already had, following one of the other guides I found) and for whatever reason this time it was as simple as advertised.

Oddly though, this time the Network Places / Samba method worked immediately as well. Looks like whatever the problem was a reboot fixed it. I'm not used to that being the case on Linux so didn't even think to try it :oops:

While we're on the topic though, am I right in thinking that the 'secure' notion in SSH implies that all traffic is going through some kind of encryption? If that's the case, would transfers be that much slower than unencrypted transfers, as asserted by [this chap on Serverfault]("http://serverfault.com/questions/18125/how-to-copy-a-large-number-of-files-quickly-between-two-servers#comment12478_18131") in relation to scp? Fair enough, someone else points out that CPU is unlikely to be a bottleneck in these situations, but since I'm likely to do this fairly often there's no reason to make it *any* less speedy than it could be.

Thanks again for your help.

---

### Post by papibe on 2012-05-19
Yes, all transfer tools that work over ssh are encrypted, because ssh encrypts its connection.

In theory, it would be slower that a plain transfer, but in practice it isn't noticeable.

Transferring large amount of data implies the time required for the transfer would be significant too. Although, the main concern of that situation may seem to be reduction of transfer time, IMHO it is not.

I believe is the main concern is data integrity, and smooth recovery from a failed transfer. 

With that in mind, rsync it is very well suited for the job.

Kind Regards.

P.S.: take a look at rsync's option --partial.
P.S.: if you're transferring large files (instead of lots of small files), take a look at option --progress.
P.S.: There are a lot of tools that can also do the job very well, most of them use either rsync in the background or the rsync algorithm.

---

