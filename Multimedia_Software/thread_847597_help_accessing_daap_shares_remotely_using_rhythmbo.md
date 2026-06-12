---
title: "help accessing daap shares remotely using rhythmbox"
date: 2008-07-02
forum: Multimedia Software
---

### Post by zeus77 on 2008-07-02
I have seen several related threads about this, like [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=187145"), [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=492293"), and [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=813109").  But none of the examples there work for me.  Here's what I have (both machines are running hardy 8.04):
[LIST]
[*]**server.somewhere.com** is the machine with all the music, running mt-daapd and ssh server.  Let's assume the daap share on this machine is called simply **server123**.  Note that any machine on server123's subnet can access the music just fine using rhythmbox, so mt-daapd is running fine when accessed within the subnet, and it plays nice with rhythmbox.
[*]**client.somewhereelse.com** is the machine running rhythmbox, and it is on a remote network.
[/LIST]
I'd simply like to be able to access the music served by server.somewhere.com using rhythmbox on client.somewhereelse.com.

Here are the commands (executed on client.somewhereelse.com) that have got me the closest so far:
```
ssh -f -g -L 127.0.0.1:3689:server123.somewhere.com:3689 -N server123.somewhere.com
avahi-publish -s -H server123.somewhere.com server123 _daap._tcp 3689 &
```

I can successfully access the (remote) mt-daapd configuration page by pointing my browser to [http://localhost:3689](http://localhost:3689), so it seems that the ssh tunnel is working correctly.  When I load rhythmbox, I do see the sharename server123 listed on the left, which would suggest that the sharename is being broadcast.  **However, I cannot browse or access any of the music in rhythmbox.  It times out and a message box says, "Cannot connect to shared music.  Cannot connect to destination.".  Does anyone have any ideas?**


Other background information for those trying to get this to work:
[LIST]
[*]You'll need to install the **avahi-utils** package do to any of this.
[*]There is some debate about whether rhythmbox can even be used to accomplish this.  Older versions of rhythmbox certainly couldn't since they couldn't browse local shares as mentioned [[COLOR="Red"]here[/COLOR]]("http://mail.gnome.org/archives/rhythmbox-devel/2006-March/msg00055.html") by the lead developer.  Post #5 [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=187145"), however, seems to suggest that with more recent versions of rhythmbox (those in gutsy and beyond), it should be no problem.
[*]Some examples I've seen for setting up the ssh tunnel use the -g flag, and others don't.  Also, some examples I've seen omit the optional "bind address" in the ssh command, i.e. 3689:server123.somewhere.com:3689, while others include it, i.e. localhost:3689:server123.somewhere.com:3689.  I am not exactly sure what the correct command should be, but be aware of this [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/61414").
[*]To help debug avahi stuff, you can browse the avahi shares by typing
```
avahi-browse -a -r -t
```
Note that I get the following (scrubbed) output when I run this command on client123.somewhereelse.com:
```
+ eth0 IPv4 server123                                     iTunes Audio Access  local
= eth0 IPv4 server123                                     iTunes Audio Access  local
   hostname = [server123.somewhere.com]
   address = [correct IP address here]
   port = [3689]
   txt = []
```[/LIST]

Thanks.
zeus77

---

### Post by elfejoyeux on 2008-07-23
Hi !

This works fine :
[http://wiki.mt-daapd.org/wiki/SSH_Tunnel](http://wiki.mt-daapd.org/wiki/SSH_Tunnel)

I use it everyday.

While building mDNS responder, you'll have to modify the Makefile in order to avoid an Error :
Just change "LD = ld -shared" to "LD = gcc -shared"

---

### Post by jcbwalsh on 2008-09-02
One alternative you might try is SimplifyMedia - [http://www.simplifymedia.com](http://www.simplifymedia.com) . Works great for me between Ubuntu and Linux Mint.

---

