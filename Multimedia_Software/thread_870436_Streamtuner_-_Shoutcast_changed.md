---
title: "Streamtuner - Shoutcast changed"
date: 2008-07-25
forum: Multimedia Software
---

### Post by spelingchampeon on 2008-07-25
Gutsy 7.10 here

I've been using Streamtuner for the last year or better, and have never had any issues with it, Streamripper or XMMS. Without conscientiously making any changes/adjustments, I turn on my PC and start up Streamtuner from which I always use Shoutcast. For some unknown reason, the far left hand column, which usually has my music choices (Metal-Rock-Pop etc etc) has disappeared to be replaced with only 2 choices..TOP STREAMS and SEARCH...thats it. No more chances to drill down to more options... nothing. Of course, if I select TOP STREAMS, it gives me about 30 choices, but nothing like it used to be. 

I've checked every setting that I could, and can not get it to reappear the way it used to be. I've removed both Streamtuner and Streamripper, but that did nothing. Does anyone have a clue?

---

### Post by markbuntu on 2008-07-25
It works fine for me, I have all the listings. Have you tried right clicking on the shoutcast tile and choosing reload?

---

### Post by spelingchampeon on 2008-08-02
I have tried to reload Shoutcast. I've attached a screenshot of the way Shoutcast appears.... 

Thanks

---

### Post by markbuntu on 2008-08-02
Do you have the stream limits button checked in Directory Preferences?

---

### Post by clubsoda on 2008-09-18
I just noticed that Shoutcast has updated their web page, which no doubt has broken Streamtuner. However the Shoutcast website has a link to the older version of their search engine at [http://classic.shoutcast.com](http://classic.shoutcast.com).

So here's my hack to redirect Shoutcast queries to the "classic" page:-```
sudo vi /etc/hosts
```
[Of course you can use nano or mousepad instead of vi.]
Add the line```
205.188.234.120 www.shoutcast.com
```and streamtuner's directory should come back online.

This redirection will affect firefox as well, so you'll no longer be able to access the "new" version of Shoutcast.  Once Streamtuner is fixed in the repositories you might want to remove that line from /etc/hosts.

---

### Post by weedwacker on 2008-10-15
Thanks, Clubsoda!

Worked for me!

Weedwacker

---

### Post by ClarkePeters on 2008-10-16
You guys on this forum just amaze me. How do you all know all these things?

so Thanks!  It worked for me too!


P.S. I noticed this thread is a little old. Does that mean no ones maintaining streamtuner and that Shoutcast will never get updated?

---

### Post by vishnu_sresht on 2008-10-18
Thanks for the help ! 

and yeah, seems that work has stopped on streamtuner.

---

### Post by offthegrid2 on 2008-10-21
I have been using 8.10 and decided to give Streamtuner a try again after it was broke in 8.04 and it works again without any problems and even uses Audacious instead of XMMS.

---

### Post by bluepowder7 on 2008-10-27
cool!  that worked nicely and quickly.
streamtuner + xmms = awesome smooth simple internet radio

---

### Post by beetlespace on 2008-10-28
You are the MAN!!

---

### Post by nufros on 2008-11-02
:confused:
Hi, I seem to be having the same problem (shoutcast tab on streamtuner emptied after reload)... I tried your solution yet couldn't figure out how to use vi, so opened 'hosts' with gedit... I inserted the line you mentioned (205.188.234.120 [http://www.shoutcast.com](http://www.shoutcast.com)) and then saved the file. Unfortunately the redirect doesn't seem to work for me... Streamtuner's shoutcast tab remains broken and I can type [www.shoutcast.com](www.shoutcast.com) into firefox and it'll still takes me to the new page...

Am I doing something wrong? Is there a specific place that line should be inserted? I made sure to save the file as "hosts" not "hosts*" or anything else...

If there's any way someone could talk me through this hack or suggest something else I'd really appreciate it, streamtuner and streamripper are great and I'd really like to keep using Shoutcast with them...

Thanks
N
--------------------------------------------------

****UPDATE

...found corrected .so file in another forum and installed it to correct problem... both of these redirect fixes don't allow the new shoutcast directories to be accessed (according to the source I found the working shoutcast.so file at...) and so are only temporary fixes until a permanent solution can be put into the repositories...\

Streamtuner needs to be maintained :P

---

### Post by beetlespace on 2008-11-09
> **nufros said:**
> 

If there's any way someone could talk me through this hack or suggest something else I'd really appreciate it, streamtuner and streamripper are great and I'd really like to keep using Shoutcast with them...



Hi nufros!

Glad to hear you got it fixed. That little problem annoyed me too! I love shoutcast and wanted very much so to have it work with StreamTuner.

I followed clubsoda's advice with one exception, I like to use nano as my editor by opening up a terminal window. (Alt + F2, then type "terminal")*
```
sudo nano /etc/hosts
```

My hosts config file looks like this**:
```

000.0.0.0 localhost
0.0.0.0 hostname
205.188.234.120 www.shoutcast.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
After you make the change he suggested, save by pressing Ctrl + O (not zero) then hit enter.Ctrl + X to exit the nano editor.

I hope this helps someone!

*Shortcut in Ubuntu to open the Run Application dialog box.
**IP info and host name changed for security reasons. :D

---

### Post by spelingchampeon on 2008-11-22
I thought I would come back here just to see if anything had happened to this post....

THANKS clubsoda ... It worked great!!

---

### Post by Gymnart on 2008-12-01
I just wanted to say, thank you clubsoda, for your workaround! It did just as you said. 

But it will only load 100 streams. I even went into the preferences and checked that "Load At Most" box and put in 782 but that did not make any difference.

Also, it only has 2 folders now (Top Streams and Search). Before it had more listing the genres to choose from.

P.S. I am not a Ubuntu user A.T.M. but my son-in-law is and it looks nice so one day, I might try it out on my machine. I would try a longer term one though. I don't like having to upgrade so frequently -- I just don't like having to deal with apps that get broken due to upgrades.

---

### Post by manosone on 2008-12-06
Well i got the same problem too.I am using streamtuner but the genre lists are empty.I reloaded the shoutcast but it only reloads the top streams and not the genre.I went to hosts and added the ip line that clubsoda said but nothing happened.Another thing i noticed is that when i did the reload on shoutcast i sow a line which was updating in streamtuner like "www.classic.shoutcast.com".
I followed the link and in the classic shoutcast site i checked a genre for example rock and nothing appeared.Then in every genre nothing appeared.Only in the top streams.On the other hand i went to the shoutcast site and all genres worked well there.


Is it anyway that streamtuner can reload and check from the shoutcast.com but not from the classic.shoutcast.com?

---

### Post by koperry on 2008-12-07
I was having some of the same problems with streamtuner. I started going to the shoutcast web page, search for my favorites, open rhythmbox and copy link location from shoutcast into new radio station in rhythmbox. A little clunky but once you set up your favorites it works.

---

### Post by greenwom on 2009-01-05
Thanks for the Fix, can this get added to the next update?  
This has been a problem since hardy....

---

### Post by hal8000 on 2009-01-20
I was about to post the same question, and found your reply, thanks beetlespace.
In Ubuntu 8.04 and 8.10 xmms no longer exists, but found that audacious with Refugee skin is a very close match.

---

### Post by capricornus on 2009-04-11
Thansk for the 205.188.234.120 [www.shoutcast.com](www.shoutcast.com)
that helped a lot.
Strange though, on my testing pc with Lenny 5, and my laptop downstairs with Antix8, it works flawlessly, only 9.04rc loads a different streamtuner, it seems.

---

### Post by frank392 on 2009-04-21
ok had the same problem plus one more whenever I press search in all categories....streamtuner will shutoff PLEASE help

---

### Post by AbdRahim on 2009-05-04
Upgraded to Ubuntu 9.04. Followed Clusoda's instructions. Worked fine at first. Today I started stramtuner and Shoutcast strems have once again disappeared.

---

### Post by Ragnar Bocephus on 2009-05-05
I think I found a more elegant solution to this problem here:  [http://tazbuntu.blogspot.com/2008/10/shoutcast-bug-in-streamtuner.html](http://tazbuntu.blogspot.com/2008/10/shoutcast-bug-in-streamtuner.html)

I downloaded the patched shoutcast.so file and dumped it in /usr/lib/streamtuner/plugins and the Shoutcast listings do show up, but they seem to still be limited to 100 streams per category.  Still, better than nothing...

---

### Post by Ntr0s on 2009-05-13
Thanks for link, yes this worked for me as well.  Might sound strange to some, but I like Streamtuner and streamripper so much, I would have re-installed Ubuntu 8.10.  Streamtuner still works natively in 8.10.  I followed the instructions in the aforementioned link, downloaded the already patched shoutcast.so plugin from the site, replaced the already existing shoutcast.so plugin with the patched plugin and PA-DOW!  Streamtuner/Streamripper/Audacious works flawlessly once again.  

Thank you!

B.

---

### Post by giorgosts on 2009-08-16
Patched shoutcast.so doesnt't work for me cause it's 32bit and my streamtuner 64. Also when I replace the URL with hexeditor as suggested, the patched plugin segfaults streamtuner.

Fortunately there is a PPA repo and its version worksforme.
[https://launchpad.net/~jensmaucher/+archive/ppa](https://launchpad.net/~jensmaucher/+archive/ppa)

---

### Post by BLTicklemonster on 2009-08-30
Thank you giorgosts. I haven't been able to listen to shoutcast on streamtuner in ages.

---

### Post by robertj20112 on 2009-09-06
> **beetlespace said:**
> Hi nufros!

Glad to hear you got it fixed. That little problem annoyed me too! I love shoutcast and wanted very much so to have it work with StreamTuner.

I followed clubsoda's advice with one exception, I like to use nano as my editor by opening up a terminal window. (Alt + F2, then type "terminal")*
```
sudo nano /etc/hosts
```

My hosts config file looks like this**:
```

000.0.0.0 localhost
0.0.0.0 hostname
205.188.234.120 www.shoutcast.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
After you make the change he suggested, save by pressing Ctrl + O (not zero) then hit enter.Ctrl + X to exit the nano editor.

I hope this helps someone!

*Shortcut in Ubuntu to open the Run Application dialog box.
**IP info and host name changed for security reasons. :D

Thanks, your advice solved my problem, too!!

---

### Post by starscalling on 2009-09-22
> **clubsoda said:**
> I just noticed that Shoutcast has updated their web page, which no doubt has broken Streamtuner. However the Shoutcast website has a link to the older version of their search engine at [http://classic.shoutcast.com](http://classic.shoutcast.com).

So here's my hack to redirect Shoutcast queries to the "classic" page:-```
sudo vi /etc/hosts
```
[Of course you can use nano or mousepad instead of vi.]
Add the line```
205.188.234.120 www.shoutcast.com
```and streamtuner's directory should come back online.

This redirection will affect firefox as well, so you'll no longer be able to access the "new" version of Shoutcast.  Once Streamtuner is fixed in the repositories you might want to remove that line from /etc/hosts.

still working in jaunty. 9-22-9

---

### Post by lprofil on 2011-04-06
This time it is not a wrong IP-problem anymore because shoutcast changed
licence and the API since December 2010 conditions:
[http://www.videolan.org/press/2010-1.html]("http://www.videolan.org/press/2010-1.html")


However there are alternatives:

[http://code.google.com/p/rhythmbox-shoutcast/](http://code.google.com/p/rhythmbox-shoutcast/)

or a rhythmbox plugin called **rhythmbox-radio-browser**
```
sudo apt-get install rhythmbox-radio-browser
```

Hope this helps someone,

Cheers,
/lprofil

---

