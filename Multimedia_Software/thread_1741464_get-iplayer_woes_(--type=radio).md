---
title: "get-iplayer woes (--type=radio)"
date: 2011-04-28
forum: Multimedia Software
---

### Post by aboontoo on 2011-04-28
Hi,

I've got a problem with get-iplayer.  I'm trying to record radio serials to listen to in my car on the daily commute.  

get-iplayer has been working fine until recently, but now, on Ubuntu, my recordings are just static 'crackle'.  They're about the right length of time, but there's no audio, just low volume, low frequency crackle.

I am on recent (<= a few weeks old) versions of everything.

I've tried:
[LIST=1]
[*]Windows version of get_iplayer - worked ok for a while, but is now refusing to record (VLC pops up, but then disappears without streaming/recording), not sure why - I need to investigate more, but would prefer an Ubuntu solution
[*][Installing rtmpdump as per other threads]("http://ubuntuforums.org/showpost.php?p=9626752&postcount=6"), no joy
[*]Changing --modes, no joy
[/LIST]

My typical command would be something like

```
get-iplayer --type=radio --force --modes=flashaac,flashaachigh,flashaacstd,flashaaclow,flashaudio,rtspaudio,rtspaacstd,rtspaaclow,wma --pid=$p
```

Though as I say, I've tried variants of the same.

I'm recording a mix of programmes, some of which are older mp3 formats, some of which are current (and hence require rtmpdump).  I've tried various combos of modes and streamers, but nothing seems to help.

Any other ideas?  I'd really appreciate a speedy response as some of the episodes I need to record are about to expire.

Many thanks in advance.  John

---

### Post by ron999 on 2011-04-28
Hi
Use the latest **get_iplayer** script from here:- [http://git.infradead.org/get_iplayer.git/shortlog/refs/heads/master]("http://git.infradead.org/get_iplayer.git/shortlog/refs/heads/master")
Test it with this command:-
```
get_iplayer --get --type=radio --pid=b010lxm5
```

---

### Post by aboontoo on 2011-04-28
Thanks Ron...

I'm possibly a tad more newbie than you might have thought.

Two more updates...

**On Windows**: I used "Save Link As" on the git repository to replace all the perl/cmd scripts on my Windows installation.  Behaviour hasn't changed.  VLC flashes up then disappears as though it has completed, but nothing has been downloaded.

Also tried running update_get_iplayer, but 'it' said that get_iplayer isn't writeable (even if I 'run as administrator').

I'm not a git/perl expert so am not clear how to drive this bit more effectively.


**On Ubuntu**: I was using get-iplayer from the Ubuntu Software Centre. Working on the principle that this is probably different to the get_iplayer available from [ftp://ftp.infradead.org/pub/get_iplayer/]("ftp://ftp.infradead.org/pub/get_iplayer/"), I downloaded and unpacked 2.79 from the latter.  However, with this I still get the same behaviour (i.e. 30 mins of static).

Any builds/alternatives?

---

### Post by ron999 on 2011-04-28
> **aboontoo said:**
> 

**On Ubuntu**: I was using get-iplayer from the Ubuntu Software Centre. Working on the principle that this is probably different to the get_iplayer available from [ftp://ftp.infradead.org/pub/get_iplayer/]("ftp://ftp.infradead.org/pub/get_iplayer/"), I downloaded and unpacked 2.79 from the latter.  However, with this I still get the same behaviour (i.e. 30 mins of static).

Any builds/alternatives?

Hi
From this page:- [http://git.infradead.org/get_iplayer.git/shortlog/refs/heads/master]("http://git.infradead.org/get_iplayer.git/shortlog/refs/heads/master")
The very top line, it says "Fix broken flashhd downloads".
Right-click 'snapshot' and 'save link as...' get_iplayer-a3ab629.tar.gz.
Then unzip it then look inside this new folder to find the file **get_iplayer**.

Use command [FONT="Courier New"]gksudo nautilus[/FONT] to explore usr/bin folder to find the installed **get_iplayer** file.
Replace it with the new one you downloaded.

---

### Post by aboontoo on 2011-04-28
I write this with my tail very tightly tucked between my legs and by way of atonement, post (to) my shame here.

Thanks for the help Ron.

I tried the fixes you suggested - to no avail.

As that didn't work, I thought I'd check back over sound card settings to see if it was something more fundamental. In doing this, I realised that the input volume control was way down.  

I set it back to 100% and hey presto, recording works fine.  As the playback on other audio was working OK, it didn't occur to  me that this was the problem.

One for the knowledge base.  Many apologies for time wasted, I owe you a beer if ever we meet.

---

### Post by gregb49 on 2011-05-06
> **aboontoo said:**
>  Many apologies for time wasted,For me, trying to get on top of internet radio, this provided some useful background, thank you

---

