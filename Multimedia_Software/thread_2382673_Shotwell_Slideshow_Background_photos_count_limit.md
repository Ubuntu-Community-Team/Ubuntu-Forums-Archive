---
title: "Shotwell Slideshow Background photos count limit"
date: 2018-01-16
forum: Multimedia Software
---

### Post by lucio-messina-w on 2018-01-16
Hi all, I have a simple question. I already searched a lot on the web but I couldn't figure out how to solve my problems.

I can [create a slideshow background using shotwell](https://askubuntu.com/questions/134/how-do-i-create-a-desktop-wallpaper-slideshow#120965), but it works for few photos only. If I select a thousand photos, all I get is a black screen as background.

So, my two questions:
1) Why is there such a limit on the number of photos of a slideshow background?
2) Is there a way to see what is the maximum number of photos allowed, and increase it?

Thank you in advance.
Best regards,
Lucio.

---

### Post by TheFu on 2018-01-16
I don't use shotwell.
I do randomly change the background/desktop on my laptop every 30min using a tiny perl script and 'feh' and cron. There's lots of ugly things in this setup, but it works.

```
#!/usr/bin/env perl
my @files=`ls -1 ~/Pictures/Best/*g`;  # yes, this is ugly and can break if filenames are _funny_
# pick a random file
my $bg = $files[rand @files];

`env DISPLAY=:0 feh --bg-scale $bg` ;

```

Calling any GUI program from cron is not likely to work, but this does. ;)

---

### Post by lucio-messina-w on 2018-01-16
Thank you, I think perl is ugly but I'll borrow from this line:
```

env DISPLAY=:0 feh --bg-scale $bg

``` 

Thank you very much :)

---

### Post by TheFu on 2018-01-16
I'm a perl guy, but for stuff like this (less than 1 screen of bash needed), I try to avoid it.  I recall doing 10 min of research for how bash could get an array of filenames and select a random element inside the array. I failed to find it, but knew exactly how to do it in perl.  Which explains the perl-based answer. ;)

If you don't quote the "$bg" in bash, funny filename characters WILL cause issues.

---

### Post by Holger_Gehrke on 2018-01-16
```

ls -1 *jpg| sed -n $(( RANDOM % $(ls -1 *jpg|wc -l) ))p|feh -bg-scale -f -

```
should set the background to a random image from the current directory. Does not work in DEs which have their own mechanism for setting the desktop image that overrides the basic X mechanism (which might be all of them except LXDE ...)

@TheFu: why use an array when you can just grab a random line of stdin ? 

Holger

---

### Post by TheFu on 2018-01-16
> **Holger_Gehrke said:**
> ```

ls -1 *jpg| sed -n $(( RANDOM % $(ls -1 *jpg|wc -l) ))p|feh -bg-scale -f -

```
should set the background to a random image from the current directory. Does not work in DEs which have their own mechanism for setting the desktop image that overrides the basic X mechanism (which might be all of them except LXDE ...)

@TheFu: why use an array when you can just grab a random line of stdin ? 

Holger

I don't use any DE. May have used this on LXDE, Mate and xfce. I don't really use those enough to know what does and doesn't work.  I'd think that only Unity would have an issue ... or any Wayland setup.  Don't know **anything** about wayland.

The 1 liner isn't clearer than the perl to me. Clearer code is more important than efficient code, almost always.  That is from my professional coding background (cmmi-5 team).  When I first wrote the script, I wasn't certain if it would be a daemon, so rereading the list-o-files may have been a weekly thing, not each instance.  My photos are organized by yyyy/mm/dd-event/, and displaying them in order is important to me. Scanning 100K image files at every program start probably isn't smart, if the startup happens every 5 min.

I alias 'ls', so that using it in bash isn't safe.  I did play with proper globbing for a few seconds in the perl, but it didn't immediately work, so I moved on.  If I were making it for someone else, I would **never use** 'ls' to create a list.

Also note that I use *g, not *jpg regex for a reason.  Some of my images are png.

Of course, there are 500 other ways to do the same time.  Mine certainly isn't the best - even for my needs - much less for others.

---

### Post by Holger_Gehrke on 2018-01-17
The shell does not expand aliases in scripts unless you set the option alias_expand with shopt, so 'ls' in a script should be fine.

Regarding the readability of the one-liner; yes, it uses arithmetic expansion (the $(( )) part) and the less often used style of command substitution ( that's $( ) instead of backticks, which I dislike for readability reasons, too easy to mistake for single quotes), but the only somewhat obscure things in it are RANDOM (a 'magic' variable which gives a different random number every time it's read) and the modulo operator '%'. My comment about no need for an array was not aimed at your perl script but at your attempt to read filenames into an array in the shell (which is not an easy thing to do; code that actually manages to do that is harder to understand than what I did ;) ). 
My code becomes easier to understand if one uses a predefined list of files (one filename per line) instead of generating the list on the fly with ls:
```
sed -n $(( RANDOM % $( wc -l listfile.txt ) ))p listfile.txt | feh --bg-scale -f -
```

And finally regarding DEs: Most modern DEs put their own undecorated  fullscreen desktop window on top of the X root window for displaying icons or other stuff on the desktop, so programs that set the background by putting an image in the X root window work just fine but you don't see the background (unless the desktop-window is set transparent and you're running a compositor to make transparency work). In xfce (which I use most of the time) setting the background with feh doesn't work, but in a simple openbox session it does.

Holger

---

### Post by lucio-messina-w on 2018-01-17
> **Holger_Gehrke said:**
> ```

ls -1 *jpg| sed -n $(( RANDOM % $(ls -1 *jpg|wc -l) ))p|feh -bg-scale -f -

```
should set the background to a random image from the current directory. Does not work in DEs which have their own mechanism for setting the desktop image that overrides the basic X mechanism (which might be all of them except LXDE ...)

@TheFu: why use an array when you can just grab a random line of stdin ? 

Holger

I know both perl and bash, I used bash a lot in the past, but now I think bash is also ugly and I tend to use Python a lot, for efficiency reasons.
Be it ugly/understandable or not, this code
```

ls -1 /path/to/the/background/images/* | sed -n $(( RANDOM % $(ls -1 /path/to/the/background/images/* | wc -l) ))p 

```

Sometimes give me this error:
```

sed: espressione -e #1, carattere 2: utilizzo non valido dell'indirizzo 0

```

which stands for
```

sed: expression -e #1, character 2: usage of the address 0 is not valid

```

I guess it's because sometimes $RANDOM is 0, so sed -n 0p gives this error.
So, the correct bash code should be:
```

ls -1 /path/to/the/background/images/* | sed -n $(( RANDOM % $(ls -1 /path/to/the/background/images/* | wc -l) +1 ))p | feh --bg-scale -f - 

```
I just added +1 :)

---

### Post by sisco311 on 2018-01-17
> **TheFu said:**
> I'm a perl guy, but for stuff like this (less than 1 screen of bash needed), I try to avoid it.  I recall doing 10 min of research for how bash could get an array of filenames and select a random element inside the array. I failed to find it, but knew exactly how to do it in perl.  Which explains the perl-based answer. ;)

If you don't quote the "$bg" in bash, funny filename characters WILL cause issues.

If you have a Bash related question, always start your research at Greg's wiki. :)

BashFAQ#26 has the answer:
```

files=(*.ogg)                  # Or *.gif, or *
n=${#files[@]}                 # For readability
xmms -- "${files[RANDOM % n]}" # Choose a random element

```

`ls' a command to list information about files (mostly in human readable format). Don't, please DON'T use it in scripts!!! /rant   :)

---

### Post by Holger_Gehrke on 2018-01-17
> **lucio-messina-w said:**
> 
I guess it's because sometimes $RANDOM is 0, so sed -n 0p gives this error.
So, the correct bash code should be:
```

ls -1 /path/to/the/background/images/* | sed -n $(( RANDOM % $(ls -1 /path/to/the/background/images/* | wc -l) +1 ))p | feh --bg-scale -f - 

```
I just added +1 :)

Yes, sed doesn't accept 0 as a line number except in ranges. Sorry, this was adapted from a quick hack I did a few weeks ago to decide which of a dozen or so movies to watch, so I only tested it once or twice. RANDOM goes from 0 to 32767, so this solution does also have a defined limit on how many images can be used.

Holger

---

### Post by lucio-messina-w on 2018-01-17
> **sisco311 said:**
> If you have a Bash related question, always start your research at Greg's wiki. :)

BashFAQ#26 has the answer:
```

files=(*.ogg)                  # Or *.gif, or *
n=${#files[@]}                 # For readability
xmms -- "${files[RANDOM % n]}" # Choose a random element

```


That's precisely why I think bash is ugly :)

---

