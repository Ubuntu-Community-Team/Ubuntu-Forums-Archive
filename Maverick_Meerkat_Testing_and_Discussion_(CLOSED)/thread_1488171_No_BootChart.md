---
title: "No BootChart"
date: 2010-05-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2010-05-19
I have two Maverick's working and today no more .png files just .tgz. Anybody have this prob or know why ? 

 Thanks

---

### Post by ranch hand on 2010-05-19
Boot chart has always been buggy for me.

Join this bug;

[https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/580560](https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/580560)

I can't believe that the 2 of us on there now are the only ones.  If enough folks join it may get fixed.

---

### Post by cecilpierce on 2010-05-19
> **ranch hand said:**
> Boot chart has always been buggy for me.

Join this bug;

[https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/580560](https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/580560)

I can't believe that the 2 of us on there now are the only ones.  If enough folks join it may get fixed.

just did an update:
The following packages have been kept back:
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins libc-bin libc-dev-bin libc6
  libc6-dev linux-generic linux-headers-generic linux-image-generic

So maybe its in the works with the held back kernel !

---

### Post by ranch hand on 2010-05-19
No, bootchart is a very small, independent app that you had to install.  There is just a problem in it some times.

If you check that bug you will see some commands to run to manually try and get the image.  This will tell you if the bug is your problem.

If you get an error saying that the .tgz file is bad then that is the bug.  If not then you should file a bug on pybootchartgui which is what creates the actual .png file from the data in the bootchart generated .tgz file.

Filing bugs is what we are here in testing for.

---

### Post by cecilpierce on 2010-05-19
sudo pybootchartgui xxx.tgz gave me the same thing, but im not hip on this stuff !
my maverick boots are abt 45 sec and the lucids are over one min.

---

### Post by ranch hand on 2010-05-19
File on that bug.  You need an account with Launchpad if you are going to be testing.  You can create it when you go to that bug.

Then click on "effects me too" and leave a comment at the bottom of the page.

You will run into a bug eventually on your box that you need to file on.  If this was that bug you would simply, in terminal, type;
```

ubuntu-bug bootchart

```
Apport would then collect information and, with your permission, send it in.  A browser tab would open to the bug page.  You would then just need to follow the directions there.

This one is easy.  You just need to confirm the thing.  They have enough work to do that they are not going to pay attention to bugs that do not effect folks that have the gumption to file bugs.

Do it.

---

### Post by ranch hand on 2010-05-20
I knew I had seen this somewhere.  9.10-testing was my first testing cycle and this was a sticky that you may find real handy;

[http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)

Maybe one of our outstanding mods will see this and update this and put it up.  I can say from experience that this was a big help.

---

### Post by MacUntu on 2010-05-20
> **ranch hand said:**
> Boot chart has always been buggy for me.

Join this bug;

[https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/580560](https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/580560)

I can't believe that the 2 of us on there now are the only ones.  If enough folks join it may get fixed.

The bug is in pybootchartgui and not in bootchart. You should mark it as invalid and join [https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/512172](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/512172)

See [http://code.google.com/p/pybootchartgui/source/detail?r=140](http://code.google.com/p/pybootchartgui/source/detail?r=140) for a quick fix. You then can generate the chart with this:```
sudo bootchart --format=png --crop-after=compiz,metacity,mutter,kwin,xfwm4 --annotate=ureadahead,mountall,hostname,hwclock --annotate=Xorg --annotate=gdm-session-worker --output="/var/log/bootchart" "/var/log/bootchart/<failing-tgz-here>"
```

---

### Post by ronacc on 2010-05-20
It looks to me like there are atleast 2 bugs , 1 in bootchart itself , it seems to be looking in the wrong place for bootchart.tgz . It is looking for /var/log/bootchart.tgz but the file is actualy in /var/log/bootchart/  and is called <yourcomputer>-#.tgz . 2 If you point bootchart at the file it extracts it but fails to display it with this message .

```
ron@ron-desktop:/var/log/bootchart$ bootchart ./1.tgz
parsing './1.tgz'
parsing 'header'
parsing 'proc_stat.log'
parsing 'proc_diskstats.log'
parsing 'proc_ps.log'
warning: no parent for pid '2' with ppid '0'
merged 0 logger processes
pruned 236 process, 0 exploders, 309 threads, and 32 runs
False
Traceback (most recent call last):
  File "/usr/bin/bootchart", line 23, in <module>
    sys.exit(main())
  File "/usr/lib/pymodules/python2.6/pybootchartgui/main.py", line 137, in main
    render()
  File "/usr/lib/pymodules/python2.6/pybootchartgui/main.py", line 128, in render
    batch.render(writer, res, options, filename)
  File "/usr/lib/pymodules/python2.6/pybootchartgui/batch.py", line 41, in render
    draw.render(ctx, options, *res)
  File "/usr/lib/pymodules/python2.6/pybootchartgui/draw.py", line 299, in render
    draw_process_bar_chart(ctx, proc_tree, times, curr_y + bar_h, w, h)
  File "/usr/lib/pymodules/python2.6/pybootchartgui/draw.py", line 319, in draw_process_bar_chart
    draw_processes_recursively(ctx, root, proc_tree, y, proc_h, chart_rect)
  File "/usr/lib/pymodules/python2.6/pybootchartgui/draw.py", line 357, in draw_processes_recursively
    child_x, child_y = draw_processes_recursively(ctx, child, proc_tree, next_y, proc_h, rect)
  File "/usr/lib/pymodules/python2.6/pybootchartgui/draw.py", line 349, in draw_processes_recursively
    draw_process_activity_colors(ctx, proc, proc_tree, x, y, w, proc_h, rect)
  File "/usr/lib/pymodules/python2.6/pybootchartgui/draw.py", line 376, in draw_process_activity_colors
    state = get_proc_state( sample.state )
  File "/usr/lib/pymodules/python2.6/pybootchartgui/draw.py", line 105, in get_proc_state
    return "RSDTZXW".index(flag) + 1
ValueError: substring not found
ron@ron-desktop:/var/log/bootchart$ 

```    

    
note ! I renamed the file to 1.tgz to save typing

---

### Post by ranch hand on 2010-05-20
There are plenty of bugs to go around in bootchart.

This one is in bootchart.

Pybootchartgui has its very own set.

Neat app but just a tad buggy.  People really need to file on these if we intend to use this bugger.

I have one install that has been around since 9.10-testing started and have removed, purged, reinstalled, cursed and anything else I could think of and it has produced a .png file twice.

Another works every time.

The rest are in between those extremes.  All on the same exact hardware.

---

### Post by MacUntu on 2010-05-20
> **ranch hand said:**
> 
This one is in bootchart.

Nope, it's clearly pybootchartgui (which draws the charts and is not just for viewing).

> **ranch hand said:**
> There are plenty of bugs to go around in bootchart.

Strange, I never had any issues with bootchart and pybootchartgui until 2.6.33, where new process states got introduced that made pybootchartgui go bye bye.

In #9 you can see that pybootchartgui tries to find the index of a state flag not in the list "RSDTZXW". Changing this to use 'find' instead of 'index' will make it return -1 instead of dying.

---

### Post by ronacc on 2010-05-20
@ ranch hand    I've been using bootchart for many dev cycles and this is the first time I have had a problem getting it to work . I'll file if the problem persists past the first couple of dailys , my current install has been acting flaky since the fresh install of lucid to start the ball rolling so I'm not going to file anything until I redo the whole thing .

---

### Post by cecilpierce on 2010-05-21
strange! yesterday i got one .png file out of six reboots, hmmm!

---

### Post by ranch hand on 2010-05-21
Yup, that is the kind of performance I get at times.  Bootchart does not generate the .tgz file correctly is the usual problem.  The commands on the bug page will tell you if that is it or not.

If it returns the result that the .tgz is corrupt then you know that is the problem.  If it returns a .png file you know the problem is with pybootchartgui.

I haven't had any trouble with pybootchartgui for quite a while.  Beginning of 10.04-testing I think was the last of that problem for me.

Do you have ATI for your video card or controller?  Seems like more trouble with some of them (like mine).

All we can do is file the bug and hope for the best.  If you joined that bug you might leave another comment.

All mine that I have checked today have actually worked (3 installs out of 5) for the first boot of the day.

---

### Post by ronacc on 2010-05-21
my first boot today did generate a .png my second boot ( after updating ) did not . I went to the bug referenced by Ranch Hand  and made the change to /usr/lib/pymodules/python2.6/pybootchartgui/draw.py  sugested by hernando in post # 5 there  , that seems to have helped with generating a .png but bootchart itself is still looking for the wrong file name .

---

### Post by cecilpierce on 2010-05-21
about the same thing as ronacc, next boot, nothing generated and my other maverick install has no png's.

---

### Post by Seventh Reign on 2010-05-21
I've also noticed that alot of times it takes up to 10-15 minutes for the PNG to appear after logging in.

---

### Post by ranch hand on 2010-05-21
> **Seventh Reign said:**
> I've also noticed that alot of times it takes up to 10-15 minutes for the PNG to appear after logging in.
Wow.   I have a lag to when it starts the generate the .png (if it is going to) and the nit takes about a minute.

I can tell when it is by watching the system monitor applet.  It winds one of my cpus up to about 25%.

I do not start boinc until that is done so as to avoid a crash.

---

