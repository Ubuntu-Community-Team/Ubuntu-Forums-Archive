---
title: "brasero error &quot;not enough space for disc image&quot;"
date: 2009-01-02
forum: Multimedia Software
---

### Post by PierreRussellStraddler on 2009-01-02
hi everyone, Pierre Russell Straddler here.

not too long ago, I got help burning CD's with brasero.  For some reason brasero couldn't read .wav files coming from Audacity.  Using the "sox" command, that problem was fixed.

Now I am trying to burn a different CD, and when I do, I get this error:

The location you chose to store the temporary image on does not have enough free space for the disc image (505 MiB needed).

(where does the temporary image get stored?)

The error outputs this log:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode deactivating
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /home/pierre/brasero_tmp_7Q9PMU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode stopping
Session error : The location you chose to store the temporary image on does not have enough free space for the disc image (505 MiB needed) (brasero_burn_record burn.c:2524)

then the drive spits out the blank CD, and the program quits.

Brasero can read (and preview) the files just fine, it just won't burn them.

:(

Any ideas?

That is problem number one.



Problem number two is related to speakers vs. headphone output.

When in audacity or brasero, the audio comes out on the external speakers.

When in Rhythmbox, the sound comes out my USB headset--the one I use for skype (except skype isn't working, it only outputs the sound to the external speakers.)

There is sound, it's just that the sound isn't always where I want it.

Does anyone know what's going on with that, or is there a post/resource/site/wiki that might help me get the headphone/speaker thing straightened out?  Naturally, I would like to use the USB headset when on skype and the external speakers with everything else (including rhythmbox.)

Thanks in advance for your help,

Pierre Russell Straddler

---

### Post by mc4man on 2009-01-02
> 
(where does the temporary image get stored?

By default brasero uses /tmp

You could run this to ck. space available

```
df -h
```

You may want to try a different app, gnomebaker or k3b come to mind.

Also there are 2 updated brasero versions, the change logs did mention some things about 'temp' though nothing specific to you. (assuming you do have enough free space.

If I was going to try one I'd go with 0.8.4

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

---

### Post by PierreRussellStraddler on 2009-01-02
Hi Mc4man!  hey--you helped me out last time!

I ran the code and I got this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              13G   12G  219M  99% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.8M  249M   2% /dev
tmpfs                 252M  308K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-9-generic/volatile

I'm guessing the Use = 99% for /dev/sda5 might be a bit of an issue...

maybe I'll try to do some tidy on the hard drive and see if that helps anything.

---

### Post by mc4man on 2009-01-03
> I'm guessing the Use = 99% for /dev/sda5 might be a bit of an issue...
I would say so, those .wav's start adding up.

If you get the opportunity at some point you might wish to do an install with more than 13gb. Space starts running low pretty quick once you get into things. (ATM you'd be hard pressed to do much of anything new (also I believe a certain amount is reserved for system use

Applications -> Accessories -> disk usage .... will show you were it went ( disregard gvfs-fuse-daemon or go edit -> preferences and uncheck it

---

### Post by cariboo on 2009-01-03
Open up an Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoremove
```

this will remove any unused depencies and clean the archived packages in /var/cache/apt/archives. Just in case in the same terminal type:

```
sudo apt-get clean
```

This will make sure that the archived packages are removed. Depending on how many updates you've done, and how many programs you have installed. you should be able to reclaim a lot of hard drive space.

Jim

---

### Post by PierreRussellStraddler on 2009-01-03
I tidied up the disk (from the command line too!) and was able to burn a CD.

problem solved!

but to keep the party going, I posted another question to the form about partition editing.  I think I am ready to remove windows from the face of my hard drive, and once that is done, will that solve the problems one encounters from a 13gb install?

I have also been enjoying the disk usage analyzer.

as always, thanks for your help

---

### Post by PierreRussellStraddler on 2009-01-03
jim--

thank you for the code.

I am keeping a book (a number of tomboy notes, anyway) of all the code people share, and it is growing every day.

it's funny you post this, as I was just wondering about that very kind of 'build up.'  In windows, they had a way to clean up the various buildup that came as a result of watching video and listening to music and what ever else on the internet.  is there a terminal command that deals with that?

Thanks for your help!



pierre russell straddler

---

### Post by hansdown on 2009-01-03
Hi PierreRussellStraddler.

cariboo907 gave you that info.

---

### Post by mc4man on 2009-01-03
> I am keeping a book (a number of tomboy notes, anyway) of all the code people share, and it is growing every day.

You can also keep a text file(s) of all of the commands you use.

```
history
```

Will show you all that's stored atm, you can copy them out every so often, notate if needed, and then clear the history.
```

history -c
```


( the easiest way to copy a long terminal is from bottom to top, then use the edit button

---

### Post by PierreRussellStraddler on 2009-01-03
Hi hansdown!

Thanks for the correction!

I tried to indicate my thanks to Jim (cariboo907) by putting the name "JIM" at the beginning of my post--but it would appear I somehow made a breech of internet ettiquite,and for that I apologize to you and to cariboo907--who was indeed most helpful!

Thanks again,

Pierre Russell Straddler

---

### Post by PierreRussellStraddler on 2009-01-03
mc4man--

yes, another helpful command!

Thanks for all your help!

Thanks to EVERYONE for all there help!

Pierre Russell Straddler

---

### Post by aztektum on 2009-02-08
Is there a way to change the path from /tmp to a different one?

---

### Post by aztektum on 2009-02-08
Awesome. I had just spent 10 minutes Googling before posting. I go back to Google while waiting to look for a reply and find this:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/319640]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/319640")

---

