---
title: "unbinding a socket/port"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by freakalad on 2009-12-08
Generally I run my system for weeks on end without a reboot (usually only reboot for new kernels), but some times the networking gets a bit... stale & the only way to fix this is rebooting :(

For example, I run a SIP client; Twinkle being my current flavor of the month. Sometimes the client may crash for no apparent reason, or because of some unforeseen bug, such as switching the use of audio output device from my headset (for VoIP) to PC speakers driven my internal sound card (for listening to music).

The app crashes out, but does not always release the port (5060), and the app will not responds to kills

`netstat -nap | grep twinkle`
```

tcp        0      0 0.0.0.0:5060            0.0.0.0:*               LISTEN      24532/twinkle   
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           24532/twinkle   
unix  2      [ ACC ]     STREAM     LISTENING     2271105  24532/twinkle       ~/.twinkle/.cmdsock
unix  3      [ ]         STREAM     CONNECTED     2275322  24532/twinkle       
unix  3      [ ]         STREAM     CONNECTED     2271083  24532/twinkle       
unix  2      [ ]         STREAM     CONNECTED     2271081  24532/twinkle

```

`ps ax | grep twinkle`
```

24532 ?        Sl     0:00 twinkle

```
& `sudo kill -s HUP 24532` or `sudo killall twinkle -v` has no effect

Any ideas please?

---

### Post by diablo75 on 2009-12-08
You said that running a killall command against the program has no effect, but does it remove it from the list of processes?  If it does, what happens if you try to restart the program you just killed?  Does it run and if so, can you close it normally without killing the process and if so, does the port free up?

It's possible there is a secondary process that runs alongside the twinkie program you're using that is responsible for the network aspect of things.  I only mention this because I use Skype, and sometimes it locks up or the audio suddenly fails, but I have to kill two seperate processes to really kill it:  skype and skype.real.  Just a possibility...

---

### Post by freakalad on 2009-12-09
I'll post that info once the problem re-occurs (restarted my X to get rid of the issue), but in short, no: the only process in play is twinkle (inspected via pstree)

Restarting Twinkle has no effect, since the app fail to load property (because it's port is bound), and whe it quits (statefully this time) it still does not release the socket.

I've seen similar issue in the past with other apps, and is often related to orphaned processes (though not in this case)

---

### Post by freakalad on 2009-12-14
Issue reoccurred again late yesterday; rebooted system after kernel update/upgrade, restarted networking (because of some other stuff) & fired up twinkle.

Ran for a bit, then became unresponsive.
Tried starting the app again, this time on a different port (5061), & then closing it down nicely, so as to try & get the stalled app to quit too.

No dice

Ran overnight with no difference: `watch -n1 "sudo killall twinkle"`

Results of `pstree -ahp` portion displaying Twinkle subset:
```

  &#9500;&#9472;twinkle,26681
  &#9474;   &#9500;&#9472;{twinkle},26714
  &#9474;   &#9500;&#9472;{twinkle},26715
  &#9474;   &#9500;&#9472;{twinkle},26716
  &#9474;   &#9500;&#9472;{twinkle},26717
  &#9474;   &#9500;&#9472;{twinkle},26718
  &#9474;   &#9500;&#9472;{twinkle},26719
  &#9474;   &#9500;&#9472;{twinkle},26720
  &#9474;   &#9500;&#9472;{twinkle},26721
  &#9474;   &#9500;&#9472;{twinkle},26722
  &#9474;   &#9500;&#9472;{twinkle},26723
  &#9474;   &#9500;&#9472;{twinkle},26724
  &#9474;   &#9500;&#9472;{twinkle},26725
  &#9474;   &#9500;&#9472;{twinkle},26738
  &#9474;   &#9500;&#9472;{twinkle},31391
  &#9474;   &#9492;&#9472;{twinkle},31392

```

In this case twinkle is only an arbitrary example, but what I'm looking for is a way to kill processes that may, for instance, have become orphaned, or that otherwise are hogging a port that I'd like to make use of again

- J

---

