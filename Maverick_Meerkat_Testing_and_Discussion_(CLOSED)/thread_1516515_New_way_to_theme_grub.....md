---
title: "New way to theme grub...."
date: 2010-06-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-06-23
With the changes in the last couple of days, grub has a new way to change the "wallpaper" & text colours.  The new lines are now 10, 11 & 12 in /etc/grub.d/05_debian_theme

#10 defines the location of the image--You need to create a /usr/share/images/desktop-base folder for your images.

#11 "normal" colour of text in the menu

#12 "highlighted" colour of text in the menu

My example now looks like:```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/ubuntu.png"
  COLOR_NORMAL="red/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=red/black
set menu_color_highlight=magenta/black
EOF
}
```I changed the lines #18 & 19 "set menu_color_normal & highlight" in case the changes to lines 11 & 12 didn't work....

It "looks" like a script will be available "sometime" in the future (grub_background.sh) to do changes--Thinking it would be interesting to make a GUI to work with this.......

---

### Post by ranch hand on 2010-06-23
That is the way I have been doing it all along although I do not change the second set which the default if no image has been found.

/usr/share/desktop-base has always been there and empty unless you install the package "desktop-base" in which case you will get the Debian grub image called for in the default image in 05_debian-theme.  It is, to me, ugly and I change it in Debian right off the bat by emptying the desktop-base folder if I do not have time for anything else.

---

### Post by autocrosser on 2010-06-23
Interesting---about a week ago during a grub update I was presented with the option to "update" my 05_debian_theme file----don't remember seeing that before...I saved the old file & it uses a very different way to change the wallpaper & menu colours.... 

OLD file:```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_blue_theme()
{
  cat << EOF
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/grub}/ubuntu.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
```

NEW file:```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/ubuntu.png"
  COLOR_NORMAL="red/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=red/black
set menu_color_highlight=magenta/black
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/grub}/ubuntu.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
```

You will see that:```
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/ubuntu.png"
  COLOR_NORMAL="red/black"
  COLOR_HIGHLIGHT="magenta/black"
fi
```is new to the file.....

---

### Post by tad1073 on 2010-06-23
> **autocrosser said:**
> Interesting---about a week ago during a grub update I was presented with the option to "update" my 05_debian_theme file----don't remember seeing that before...I saved the old file & it uses a very different way to change the wallpaper & menu colours.... 

OLD file:```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_blue_theme()
{
  cat << EOF
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/grub}/ubuntu.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
```NEW file:```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/ubuntu.png"
  COLOR_NORMAL="red/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=red/black
set menu_color_highlight=magenta/black
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/grub}/ubuntu.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
```You will see that:```
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/ubuntu.png"
  COLOR_NORMAL="red/black"
  COLOR_HIGHLIGHT="magenta/black"
fi
```is new to the file.....

that has always been in grub2, the only change I saw was that "SOURCE" was replaced with "."

---

### Post by autocrosser on 2010-06-23
Really--the grub2 file that is the "old" file is from my reinstalled Lucid right after final & then updated to Maverick...And it looks like quite a chunk of code was changed.....I can .tar both files for anyone to look at if wished.......

---

### Post by ranch hand on 2010-06-23
That should not have been the case.  The "grub" file was left over from 9.10.

---

### Post by autocrosser on 2010-06-24
I guess that I'm not clear enough--When I talk about "grub" I'm talking about grub2--I was one of the early testers for grub2 & have left Legacy Grub very far behind.....

In any case---the bit I'm talking about is the code snip I posted thirdly....compare file #1 & file #2 & you will see that the snip I noted is a change--I goto my backup install (two weeks old--not updated) & find the 05_debian_theme is just like my posted "old" file.......so I must conclude that it is a change that was introduced less than two weeks ago.


This is the relevant snip from my Maverick install that has not been updated for more than two weeks:```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

```

---

### Post by ranch hand on 2010-06-24
I am aware of this, believe me.   I even remember when we all had so much fun in 9.10-testing when they threw grub2 at us with A2 with no real documentation.  A FUN time was had by all.

---

### Post by autocrosser on 2010-06-24
More info in prior posting.....

---

### Post by ranch hand on 2010-06-24
This is very interesting.

This is not from 10.10 but from a clean install of 10.04;
```

!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/menu.png"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="yellow/black"
fi

```
Yes I have changed the image and the font colors.  I made no other changes.  I really haven't seen a /usr/share/grub file since 9.10 or very early in 10.04 testing maybe.

That 10.04 was installed using the CD from the final RC ISO for 10.04 used in ISO testing.

---

### Post by ranch hand on 2010-06-24
Ah, did you install the package of images for grub?  That will change your 05_debian-theme file and install the grub file in images.

I have used my own since I realized what they were calling fore in the default script.  Never liked the ones in the package.

Besides, in 9.10 gimp was a standard install.

---

### Post by tad1073 on 2010-06-24
below is a link to a video I uploaded to youtube with customized grub, gdm etc...

[http://www.youtube.com/watch?v=Aa45wNpJ3yU](http://www.youtube.com/watch?v=Aa45wNpJ3yU)

---

### Post by felixsays on 2010-07-10
> **autocrosser said:**
> ```


....

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi
```

It could be noted that this "find usable backgrounds" code doesn't do what it seems to suggest it does, which is "Automatically find any usable background in the case that one has not already been specified."

In particular, changing the for loop in this line```
  for i in  {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}  ; do
```to the following
```
  for i in  {/boot/grub,/usr/share/images}/*.{png,tga,jpg,jpeg}   ; do
```will actually search those directories for any file ending in png,tga,jpg,jpeg and use that file as the background image. I have to imagine this is something closer in intent.

Just a thought.

---

### Post by ranch hand on 2010-07-10
The background files seem to work best as .png and at 640x480, therefore it is simpler to just add them to the desktop-base file.

I am lazy and use the same file name for the image used (menu.ping) and just have several ready for the name change in /usr/share/images.

The way it is set up in Debian is that there are several (10 to 15 somewhere in that range) in the desktop-base file including, of coarse, moreblue-orbit-grub.png.  That way you can just change the file name.

---

### Post by Starks on 2010-07-10
GRUB maintainers should just incorporate the BURG code.

---

### Post by cecilpierce on 2010-07-11
> **Starks said:**
> GRUB maintainers should just incorporate the BURG code.

I agree, theres even a new GUI called "BURG MANAGER".
Haven't tried it yet but it looks nice, anyone tried it yet ?

---

### Post by ranch hand on 2010-07-11
I have run Burg and think it is a really great piece of work.  I can not use it however.

I run with nothing but a custom menu file and Burg does not support that well.

There are also folks, like myself, who do not want icons on the menu or other visual gymnastics.

I think that Grub is fine just the way it is.

Burg appears to get better at what it does all the time.  I need to install in on one of my installations again and see where it is now.  Really interesting (and good) work on that.  I just do not have the good taste to really want it.

---

### Post by cecilpierce on 2010-07-11
> **ranch hand said:**
> I have run Burg and think it is a really great piece of work.  I can not use it however.

I run with nothing but a custom menu file and Burg does not support that well.

There are also folks, like myself, who do not want icons on the menu or other visual gymnastics.

I think that Grub is fine just the way it is.

Burg appears to get better at what it does all the time.  I need to install in on one of my installations again and see where it is now.  Really interesting (and good) work on that.  I just do not have the good taste to really want it.

Check out BURG Loader Forum if you have any probs or questions with it. Ive been using the custom file you posted awhile back with burg and its working great. You could install burg on a flash drive like I did just in case something goes hay-wire you won't mess up your original install.

---

### Post by Starks on 2010-07-11
> **cecilpierce said:**
> I agree, theres even a new GUI called "BURG MANAGER".
Haven't tried it yet but it looks nice, anyone tried it yet ?
Thanks for informing me about this exciting development.

---

### Post by cecilpierce on 2010-07-11
> **Starks said:**
> Thanks for informing me about this exciting development.

Yea, I wonder why the GRUB guys don't get wind of this?

---

### Post by autocrosser on 2010-07-11
> **cecilpierce said:**
> Yea, I wonder why the GRUB guys don't get wind of this?

Because they don't want to admit that there are any good ideas but their own:frown:

---

### Post by ranch hand on 2010-07-11
It could be that they are more interested in removing the current bugs in Grub and getting os-prober to work better.

I know os-prober is a separate project but there seems to be no movement there.

If you are set up like I am with 10 linux installations on this drive, for instance, all using the same custom file you find that os-prober lists every OS on every partition.  As you can imagine, this adds up to a large grub.cfg (or burg.cfg).  This is the main reason I disable os-prober first thing when doing an install.

---

### Post by cecilpierce on 2010-07-11
yea os-prober is a mess for me so is 10_linux, all i have executable now is 00_header and 06_custom.

---

### Post by SevenMachines on 2010-07-11
> **ranch hand said:**
> It could be that they are more interested in removing the current bugs in Grub and getting os-prober to work better.

i think that may be the point, the first priority of a boot loader is that it works, prettiness is good but, first things first! gfxmenu works well for me to be honest, probably needs a little TLC but its nice enough for that 3 second timeout :)

---

### Post by 23dornot23d on 2010-07-12
> **ranch hand said:**
> It could be that they are more interested in removing the current bugs in Grub and getting os-prober to work better.

I know os-prober is a separate project but there seems to be no movement there.

If you are set up like I am with 10 linux installations on this drive, for instance, all using the same custom file you find that os-prober lists every OS on every partition.  As you can imagine, this adds up to a large grub.cfg (or burg.cfg).  This is the main reason I disable os-prober first thing when doing an install.

I have a  very similar set up to you Ranch Hand .... 
In the fact that I have a similar number of menu choices 

How do you stop GRUB2 destroying what you have set up .......
can I import the Mint Grub2 settings over here somehow  ? 
not sure how I stop the prober in the updates ... upgrades .... 

So when doing my upgrades ..... it just seems to overwrite everything I have set up
The problem is it does not appear to give me any choice along the way  ..... or ask if I have
another menu already set up .... 

GRUB2 update in safe-upgrades kills off most of my [System]("http://sites.google.com/site/problems7730zg/gnome-3") ..... 

I was testing but now 
I cannot run MUTTER or GNOME3 why would GRUB2 make such a difference .......

ITS PURPOSE IN LIFE - IS A MENU ..... TO PICK MY OS of CHOICE.

[URL="http://sites.google.com/site/problems7730zg/home/grub-2-problem-of-other-operating-systems-wanting-to-overwrite-the-good-one"]This is my full report as I go through it ..... I will fix it again ....... and try to show what is Wrong

[/URL]

---

### Post by ranch hand on 2010-07-12
> **23dornot23d said:**
> I have a  very similar set up to you Ranch Hand .... 
In the fact that I have a similar number of menu choices 

How do you stop GRUB2 destroying what you have set up .......
can I import the Mint Grub2 settings over here somehow  ? 
not sure how I stop the prober in the updates ... upgrades .... 

So when doing my upgrades ..... it just seems to overwrite everything I have set up
The problem is it does not appear to give me any choice along the way  ..... or ask if I have
another menu already set up .... 

GRUB2 update in safe-upgrades kills off most of my [System]("http://sites.google.com/site/problems7730zg/gnome-3") ..... 

I was testing but now 
I cannot run MUTTER or GNOME3 why would GRUB2 make such a difference .......

ITS PURPOSE IN LIFE - IS A MENU ..... TO PICK MY OS of CHOICE.

[URL="http://sites.google.com/site/problems7730zg/home/grub-2-problem-of-other-operating-systems-wanting-to-overwrite-the-good-one"]This is my full report as I go through it ..... I will fix it again ....... and try to show what is Wrong

[/URL]
This is not really the place for this.

I have no trouble with updates at all.  I have /etc/grub.d/00_header, /05_debian-theme and /06_custom enabled as executable.  Don't us the Memtest, don't need the rest.

I have actually purged grub-pc and grub-common, reinstalled and besides having to disable the ones I don't use every thing was fine.  Purge doesn't touch any but the default files so 06_custom is safe.

Symbolic menu entries do not need updates (ever), MS menu entry is a chainloader (if you have that crap on your box - I won't) so there should never be a problem.  Mac I know nothing about but would assume it would be a chainload too.

---

### Post by 23dornot23d on 2010-07-12
I noticed that you had a similar setup , so thought you might experience similar things.

---

### Post by arrimapirate on 2010-07-13
I can not get a grub2 theme to work at all. I placed a 640x480 image called "world.png" in my /usr/share/images/desktop-base folder and changed my code to:

> 
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/world.png"
 COLOR_NORMAL="red/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=red/black
set menu_color_highlight=magenta/black
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in ${/boot/grub,/usr/share/images/desktop-base}/world.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi


After running "sudo update-grub" and restarting, it gives me the same black and white grub menu. Any ideas why?

---

### Post by cecilpierce on 2010-07-13
this is my debian_theme file from june 4, the word "source"(line4) is missing on yours, not sure if it means much but i remember another thread about that.


# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/gnome1.png"

mine seems to work fine.

---

### Post by Reiger on 2010-07-13
Yes it does. The source line executes the script in the context of the theme script (so variables in the theme are available to the source'd script and vice versa).

---

### Post by arrimapirate on 2010-07-13
I added the word source to line 4
I noticed two things: 
1. the 05_debian_theme is not marked as executable. I fixed that.
2. I was missing the line "source /usr/lib/grub/grub-mkconfig_lib" which is in my other debian theme files. When i added this line and then run update-grub i get this error > /etc/grub.d/05_debian_theme: 3: source: not found

---

