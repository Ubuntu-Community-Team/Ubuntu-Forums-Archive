---
title: "XMLTV Error 2304"
date: 2009-02-08
forum: Mythbuntu
---

### Post by nunrgguy on 2009-02-08
Any ideas about this one?
Error was originally 6400 and has been for the past week. I deleted supplement folders and the error changed to 2304 but no grab still took place, in this situation xmltv is supposed to use the channels.dat file from cache? Looking at the cache files some of them had different permissions. I cleared all the cache files but still no grab takes place - has RT created an empty channeld.dat at their end or is there something wrong at this end. I cannot run mythfilldatabase in debug mode - I get the message about not being able to run in quiet in debug.

Log:

Bad channel entry seen in RT channels.dat: 	 at /usr/bin/tv_grab_uk_rt line 490.
2009-02-08 17:31:46.772 FAILED: xmltv returned error code 2304.
2009-02-08 17:31:46.773 Error in 1:1: unexpected end of file
2009-02-08 17:31:46.773 Updating icons for sourceid: 1

---

### Post by `Zidane on 2009-02-08
hey there, i have had exactly this same problem, and fixed it (i'm sure an update will be released shortly, but for now, there's a quick fix).  i should point out, i do not use mythbuntu, i use kubuntu and maxemum tv guide, however both use xmltv to get their listings.

the error occurs in the perl script /usr/bin/tv_grab_uk_rt because it does not recognise a line in the channels.dat file retreived from the RT site.  this is because they appear to have added a "personal use only" header to the file recently.

anyways...   the quick fix.

1.  you need to make the script editable with this command
```
sudo chmod a+w /usr/bin/tv_grab_uk_rt
```

2. once that is done, open the file with your favourite text editor (kate rocks!).

on line 490, you should see....
```
486: my $need_final_update = 0;
487: my $num_good_rt_channels;
488: foreach (@rt_channels) {
489:    chomp;
490:    /^(\d+)\|(.+)/ or die "Bad channel entry seen in RT channels.dat: $_";
491:    my ($rt_id, $rt_name) = ($1, $2);
492:    if ($seen_rt_id{$rt_id}++) {
```
**note:  i have added line numbers for ease of use, the line numbers are not in the file, they are shown by your editor.**

3.  change line 490 as follows
```
485: my $need_final_update = 0;
486: my $num_good_rt_channels;
487: foreach (@rt_channels) {
489:    chomp;
490:    #/^(\d+)\|(.+)/ or die "Bad channel entry seen in RT channels.dat: $_";
491:    /^(\d+)\|(.+)/ or next;
492:    my ($rt_id, $rt_name) = ($1, $2);
493:    if ($seen_rt_id{$rt_id}++) {
```

this means making two changes.
```

change 1: add a # at the start of line 490
change 2: add the following line just after (on line 491)
          /^(\d+)\|(.+)/ or next;

```

once these changes are completed, save the file and close your editor.

3.  now we need to turn off the editable permission we turned on in 1. with this command
```
sudo chmod a-w /usr/bin/tv_grab_uk_rt
```

and now, lo and behold, tv_grab_uk_rt is happy again.

**what this change will actually do**
the "regex or die" command on line 490 means "see if i recognise this line, if i do not, fall over and scream until someone comes to fix me".

after changing this, it becomes "regex or skip", if it does not recognise the line, it simply ignores it and skips on to the next one and carries on processing the tv listings.


this should be considered a temporary fix as i am sure the ubuntu team are merrily working away on a patch for the next set of updates.

hope this helped :)

---

### Post by rosera on 2009-02-09
Nice one, I ran my weekly update last night and noticed this error. Added your amendment and it went through with a problem. cheers :p

---

### Post by nunrgguy on 2009-02-09
Awesome fix. Thanks:guitar:

---

### Post by `Zidane on 2009-02-09
hehe, glad i could help, i know what a pain it is to suddenly be without tv listings. :)

---

### Post by elp99jcm on 2009-02-13
Excellent, thanks for you quick fix. It works a treat. 

The xmltv grab from RT does seem rather flaky so it makes sense to avoid anything that dies when a bad line is encountered.

Any idea why the xmltv release nightly status seems to run without errors?

---

### Post by Guinch on 2009-02-17
Great! Thought I'd have to spend tonight muddling through this, but fixed in 5 min thanks to you. Cheers!

---

### Post by `Zidane on 2009-02-17
> **elp99jcm said:**
> Excellent, thanks for you quick fix. It works a treat. 

The xmltv grab from RT does seem rather flaky so it makes sense to avoid anything that dies when a bad line is encountered.

Any idea why the xmltv release nightly status seems to run without errors?

i looked at the cvs on sourceforge for the uk grabber, it looks like someone has almost completely rewritten it to make it much more robust.  it seems much nicer now, we just have to wait for them to release and no doubt the ubuntu or mythbuntu folks will package us up a new one.

---

