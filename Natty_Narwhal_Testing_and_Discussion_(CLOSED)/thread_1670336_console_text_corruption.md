---
title: "console text corruption"
date: 2011-01-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sirjasonr on 2011-01-18
Hello all you wonderful ubuntu-loving people :)

I am just after a little bit of help with fixing a text corruption issue / advice for filing a bug report (if necessary).

So, generally speaking the stability I am experiencing with Natty is as I expect; I'm fully aware that this is a very very early development release and so all sorts of things can go wrong. So let's not be mean to me about that... I totally get the risks involved etc. etc. I just wanted to point that out ;)

So while Gnome/Unity are up and running, graphics run more or less perfectly, the boot process text is completely garbled and if after everything is fully loaded I hit Control+Alt+F1-F6 the text looks like:
* [this]("http://picasaweb.google.com/lh/photo/uv-jTmc_9p_ZArZytBTBDTZf4cZWJILkBmYHchZ4xbc?feat=directlink")
* [the above image close-up]("http://picasaweb.google.com/lh/photo/L1hVdV31O29Bi7bBrD0b5DZf4cZWJILkBmYHchZ4xbc?feat=directlink")
The above links are supposed to be of the ubuntu login prompt.

The problem occurred after running the upgrade command:
```
sudo do-release-upgrade -d
```
As is standard upgrade procedure.

My graphics card is reported by lspci to be: 
```
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

```

Is there anything obvious going on that I can tweak to make it all happy again?

Since I have a working GUI, it's not super important for me to fix it in a rush... so if it's a matter of simply waiting for updated packages, then so be it. But any advice on the matter would be fantastic!

Cheers,
Jason

---

### Post by cariboo on 2011-01-18
Have a look at console-setup in /usr/share/console-setup, there was an upgrade about a week ago or so.

BTW to create a bug report, you can press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

---

### Post by VMC on 2011-01-18
Yes, your text display looks like what I get when I accidentally cat out a binary file. 
Usually though just a restart fixes it.
 I couldn't find out what country your from. Are you using USA type keyboard?

---

### Post by sirjasonr on 2011-01-18
Thanks for your reply!
Okay so the console-setup looks fine... I can't see anything that would stop the text from showing normally. It looks like this:
```
# Change to "yes" and setupcon will explain what is being doing
VERBOSE_OUTPUT=no

# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

# Put here your encoding.  Valid charmaps are: UTF-8 ARMSCII-8 CP1251
# CP1255 CP1256 GEORGIAN-ACADEMY GEORGIAN-PS IBM1133 ISIRI-3342
# ISO-8859-1 ISO-8859-2 ISO-8859-3 ISO-8859-4 ISO-8859-5 ISO-8859-6
# ISO-8859-7 ISO-8859-8 ISO-8859-9 ISO-8859-10 ISO-8859-11 ISO-8859-13
# ISO-8859-14 ISO-8859-15 ISO-8859-16 KOI8-R KOI8-U TIS-620 VISCII
CHARMAP=UTF-8

# The codeset determines which symbols are supported by the font.
# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian
# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3
# Vietnamese.  Read README.fonts for explanation.
CODESET=Lat15

# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes
# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes
# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14
# and 16) and Fixed (sizes 13, 14, 15, 16 and 18).  Only when
# CODESET=Ethiopian: Goha (sizes 12, 14 and 16) and
# GohaClassic (sizes 12, 14 and 16).
# Set FONTFACE and FONTSIZE to empty strings if you want setupcon to
# set up the keyboard but to leave the console font unchanged.
FONTFACE=VGA
FONTSIZE=16

# You can also directly specify nonstandard font or console map to load.
# Use space as separator if you want to load more than one font.
# You can use FONT_MAP in order to specify the Unicode map of the font
# in case the font doesn't have it embedded.

# FONT='lat9w-08.psf.gz /usr/local/share/braillefonts/brl-08.psf'
# FONT_MAP=/usr/share/consoletrans/lat9u.uni
# CONSOLE_MAP=/usr/local/share/consoletrans/my_special_encoding.acm

# You can also specify a screen size that setupcon will enforce.  This can not
# exceed what the current screen resolution can display according to the size of
# the loaded font.
# 
# SCREEN_WIDTH=80
# SCREEN_HEIGHT=25
```

But I did notice one interesting thing: If my computer boots normally, the console corruption occurs. However, if the boot process is interrupted and the computer restarted, selecting the default kernel from the GRUB menu that shows as a consequence of the interrupted boot results in no corruption and everything is fine. But if I force the GRUB menu to show by pressing Shift just after the BIOS POST finishes, selecting the default kernel still causes console text corruption. Any hints there with where to look next? A very bizarre problem, if you ask me.

I have saved copies of the DMESG output from a where the console is working and when it isn't. At first glance, I notice one main difference...
Corrupt console:
```
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
```
Working console:
```
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
```

I've attached these files for viewing. Edit: I tried to attach these files for viewing but they're too big.

Jason

---

### Post by sirjasonr on 2011-01-18
> **VMC said:**
> Yes, your text display looks like what I get when I accidentally cat out a binary file. 
Usually though just a restart fixes it.
 I couldn't find out what country your from. Are you using USA type keyboard?

I'm from Australia with a US keyboard. My console is crying binary :(

---

### Post by ronacc on 2011-01-18
it looks like you are printing ascii graphics instead of text , your console -setup is identical to mine with the exception of the font face , I switched my fontface to match yours but could not duplicate your problem , check what keymap is being loaded and make sure it matches your keyboard .

---

### Post by sirjasonr on 2011-01-20
How do I go about checking the keymap? Any ideas why I might be experiencing the strange behaviour when I boot in the way described in my previous post?

If anyone feels like going through my dmesg output for my successful and unsuccessful boot (with respect to console text corruption), I've uploaded them here:
* [corrupted text dmesg log]("https://docs.google.com/document/d/185nbuY2Y5QQH3kNTeIBF0bvjVpnfiDCcOnzPR7rIP48/edit?hl=en_GB&authkey=COjM2YIJ")
* [working]("https://docs.google.com/document/d/12OQbjd8SLUUyh4omklQ5VDDfBDLN2ATMgXAcUgzUUac/edit?hl=en_GB&authkey=CNWB7JoB")

There is an option to download these files from Google Docs as text for easier processing.

By the way, ronacc, thanks for trying to replicate my problem! The time taken to do so is really appreciated.

---

