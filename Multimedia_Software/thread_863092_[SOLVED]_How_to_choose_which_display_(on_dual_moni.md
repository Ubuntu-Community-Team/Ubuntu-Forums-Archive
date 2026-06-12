---
title: "[SOLVED] How to choose which display (on dual monitor) when starting a program"
date: 2008-07-18
forum: Multimedia Software
---

### Post by Paddy Landau on 2008-07-18
I have two screens (dual monitor).

Generally, X11 chooses on which screen to start a program, and it's quite sensible about it.

However, there are a couple of programs that I always want to start on a specific display.


[LIST=1]
[*]Sometimes, a program specifically has an option for this. For example, firefox has a startup option [COLOR=Navy]--display=DISPLAY[/COLOR]. In this case, what do I put as DISPLAY? I tried [COLOR=Navy]firefox --display=0[/COLOR] and [COLOR=Navy]firefox --display=VGA[/COLOR], but neither works ("Error: cannot open display: 0").
[*]What about if a program doesn't have a specific option for the display? Is there a way to specify in which screen to start the program?
[/LIST]

---

### Post by Paddy Landau on 2008-07-24
Bump?

---

### Post by northern lights on 2008-07-24
Edit the launcher(s) for these apps. In the box titled "Command:" enter ```
DISPLAY=:0 ACTUAL COMMAND
```where ACTUAL COMMAND is what is already written there.

For the other monitor, make it "DISPLAY=:1"

---

### Post by Paddy Landau on 2008-07-25
Thanks for the advice.

Unfortunately, it doesn't work. I've used firefox as the test program.

[LIST]
[*]From the Terminal:
[LIST]
[*]"[COLOR=Navy]DISPLAY=:0 firefox[/COLOR]" and "[COLOR=Navy]firefox --display=:0[/COLOR]" both start firefox in the secondary monitor.
[*]"[COLOR=Navy]DISPLAY=:1 firefox[/COLOR]" and "[COLOR=Navy]firefox --display=:1[/COLOR]" both return the error, "[COLOR=Navy]Error: cannot open display: :1[/COLOR]".
[/LIST]
 
[/LIST]

[LIST]
[*]From the menu:
[LIST]
[*]"[COLOR=Navy]DISPLAY=:0 firefox[/COLOR]" returns the error, "[COLOR=Navy]Failed to execute child process "DISPLAY=:0" (No such file or directory)[/COLOR]".
[*]"[COLOR=Navy]firefox --display=:0[/COLOR]" opens firefox in the secondary monitor.
[*]"[COLOR=Navy]DISPLAY=:1 firefox[/COLOR]" returns the error, "[COLOR=Navy]Failed to execute child process "DISPLAY=:1" (No such file or directory)[/COLOR]".
[*]"[COLOR=Navy]firefox --display=:1[/COLOR]" does nothing (presumably because of the error).
[/LIST]
 
[/LIST]
Is there, perhaps, some sort of setup I have to do first?

---

### Post by northern lights on 2008-07-25
How about "DISPLAY:=0.1" instead of "...:=1"?!

---

### Post by Paddy Landau on 2008-07-25
I must have something incorrectly set up.
I get an error for every one of the following.

[LIST]
[*]DISPLAY=:0.1
[*]DISPLAY=:0.2
[*]DISPLAY=:1.0
[*]DISPLAY=:1.1
[*]DISPLAY=:1.2
[/LIST]
However, the following (default value) does work, albeit on the secondary monitor.

[LIST]
[*]DISPLAY=:0.0
[/LIST]
Do you know where this is documented? I don't find it in *man* (presumably I'm looking in the wrong places).

---

### Post by unutbu on 2008-07-25
When you have two monitors, X treats them as one display with (DISPLAY=:0.0) with a big resolution. You can control the location of some apps by using a "geometry" flag. For instance:

```
gnome-terminal --geometry=100x20+500+500
```

will open a gnome-terminal which is 100 characters wide, 20 charactors long (vertically), and which has its upper left corner set at pixel coordinate (500,500).

Firefox, on the other hand, is notoriously obstinant -- FF has no geometry flag.

There is a package, devilspie, which can give you a lot of control over where all windows appear, however. I don't use devilspie, so I can't give you specific instructions, but these might point you in the right direction:

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)
[http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)
[http://ubuntuforums.org/showthread.php?t=634048](http://ubuntuforums.org/showthread.php?t=634048)

---

### Post by Paddy Landau on 2008-07-26
Thanks for the information.

Devil's Pie is a fairly complex system, and I'll require a fair bit of experimentation to get it to work.

I also found a GUI interface to it from Google:
[http://code.google.com/p/gdevilspie/](http://code.google.com/p/gdevilspie/)
That's a help, too.

I've installed devilspie and gdevilspie and will slowly learn it.

---

### Post by Paddy Landau on 2008-07-26
Hmm...

I've installed devilspie and gdevilspie, and experimented.

Devil's Pie works, but only on existing windows when it starts up. It doesn't work on new windows.

For example, if I start devilspie and then open Firefox, then Firefox opens in its usual place. But, if I then kill devilspie and restart it, then it moves Firefox's window to the right place.

Do you know how I fix this problem and get devilspie to work on all windows created *after* devilspie has started running?

(Strange name, "Devil's Pie"!)

---

### Post by unutbu on 2008-07-26
Please post your devilspie script.
Not sure that I can help, but I'll see if I can get it to work on my machine...

---

### Post by Paddy Landau on 2008-07-27
> **unutbu said:**
> Please post your devilspie script.
Not sure that I can help, but I'll see if I can get it to work on my machine...
Here it is. It was automatically generated by gdevilspie. As I said, it works if I kill devilspie and restart it (on the existing windows only). The indentation is mine; the original doesn't have it.
```
; generated_rule Thunderbird - open email
( if 
  ( and 
    ( is ( application_name ) "Thunderbird" )
    ( matches ( window_name ) ".*- Thunderbird" )
  ) 
  ( begin 
    ( geometry "890x970+1400+0" )
    ( println "match" )
  )
)
```Thanks for looking at this for me.

---

### Post by unutbu on 2008-07-27
Try replacing your current script with this:
```

(debug)
( if 
  ( is ( application_name ) "Thunderbird" )
  ( begin 
    ( geometry "890x970+1400+0" )
  )
)

```

If it doesn't work:
Open a terminal and type:
```
killall devilspie
devilspie
```
Open a thunderbird window to exhibit the problem.
Then post the output from devilspie.

If it does work:
Take out the (debug) line from the script and you should be good to go.

---

### Post by Paddy Landau on 2008-07-27
Interesting. When I started devilspie, it gave the following output, clearly related to those windows already open.
```
got eof
Window Title: 'paddy@paddy-ubuntu: ~'; Application Name: 'paddy@paddy-ubuntu: ~'; Class: 'Gnome-terminal'; Geometry: 1280x800+0+224

** (devilspie:13329): CRITICAL **: e_sexp_eval: assertion `f->tree != NULL' failed
Window Title: 'Inbox - Thunderbird'; Application Name: 'Thunderbird'; Class: 'Thunderbird-bin'; Geometry: 1280x1000+1280+0

** (devilspie:13329): CRITICAL **: e_sexp_eval: assertion `f->tree != NULL' failed
Window Title: 'Desktop'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 2560x1024+0+0

** (devilspie:13329): CRITICAL **: e_sexp_eval: assertion `f->tree != NULL' failed
Window Title: 'Bottom Expanded Edge Panel'; Application Name: 'Bottom Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1280x24+1280+1000

** (devilspie:13329): CRITICAL **: e_sexp_eval: assertion `f->tree != NULL' failed
```Then, when I opened a new email, it gave the following extra output.
```
Window Title: 'Mozilla Thunderbird'; Application Name: 'Thunderbird'; Class: 'Thunderbird-bin'; Geometry: 900x800+1280+0

** (devilspie:13329): CRITICAL **: e_sexp_eval: assertion `f->tree != NULL' failed
```I don't know where to look up these "CRITICAL" codes; do you? I don't find any troubleshooting or error codes anywhere in the official Devil's Pie pages.

---

### Post by Paddy Landau on 2008-07-27
Stop press...

It's working, despite those messages!

I'll now experiment to find out where I went wrong, and post the results once I've found out.

---

### Post by overdrank on 2008-07-27
Moved to Multimedia & Video :)

---

### Post by Paddy Landau on 2008-07-27
> **Paddy Landau said:**
> I'll now experiment to find out where I went wrong, and post the results once I've found out.
I have to thank you for pointing me in the right direction.

It seems that when Thunderbird opens a window, it opens it as one name and immediately renames it. Thus, my initial condition, which included the window name, was causing Devil's Pie to skip it.

Thanks again!

---

### Post by mixmastamyk on 2011-01-05
Been wrestling with the same problem and was able to beat Thunderbird into submission like so.  Doesn't need a background process either.  Put this into the launcher icon:

> [FONT=Courier New]sh -c "thunderbird %u & sleep 3;  wmctrl -r thunderbird -b remove,maximized_vert,maximized_horz; wmctrl -r thunderbird -e 0,1920,0,1200,1600"[/FONT]

---

### Post by BicyclerBoy on 2011-01-05
If you use separate x screens for each display then the DISPLAY variable works..

This is a config option for nvidia X server.

Most apps stay on the screen they are launched from etc..
Complete video mode independence etc..

---

