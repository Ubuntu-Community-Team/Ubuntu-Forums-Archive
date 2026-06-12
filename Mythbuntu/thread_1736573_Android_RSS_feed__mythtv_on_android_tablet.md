---
title: "Android RSS feed / mythtv on android tablet"
date: 2011-04-22
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-04-22
hey folkes;

So i am trying to get mythtv working on my android HD2 with a view to getting a android3 tablet (xoom or 10galaxcy i think).

After a fair bit of google searching the following is about the only option i have found;

[http://www.mythtv.org/wiki/Android_RSS_Video_Feed](http://www.mythtv.org/wiki/Android_RSS_Video_Feed)

Not the most elegant solution but looks like it should work.  Does anyone else have some suggestions?  

(Also, can someone help me with the global variables in the script, which folders do i need to set against;

my $mythdir = '/data/mythtv';
my $feedsdir = "$mythdir/feeds";
my $outdir = "$feedsdir/recordings/";

And when it asks for my domain can i just put the machines IP address?  

my $url = "http://www.mydomain.com";

Thanks, i am guessing i am not the only person that would like a myth frontend on a 10inch tab.

Andy

---

### Post by lk06oem on 2011-05-02
Mythbuntu has a dnla server built in. I can't remember if it needs turning on or configuring though. There is a dnla client that works on the xoom: UNPnPlay it shows all the recordings on the backend. The big bummer is that the xoom does not have decent video player that can play mpg files, that UK Freeview broadcasts. It plays mp4 files fine streaming over the network.

---

### Post by nickrout on 2011-05-03
mythexport is the answer

---

