---
title: "Nvidia-settings crashes when I touch the overscan slider"
date: 2011-11-22
forum: Multimedia Software
---

### Post by htt-thalan on 2011-11-22
Hi People,

in our bedroom we have an old Philips 100hz CRT tv for the occasional cartoon or show on tv. We don't use it thát often because we have LCD + Digital HDTV downstairs. 

So I stuffed together some old parts to create a lightweight rig to play my downloaded series on the old beastie now and then. It's a P4 with 1gb of ram and a Geforce 5200 PCI I had lying around, because it still has an analog output besides the VGA connector. I'm using the CRT as it's primary and only display.

It's running Lubuntu 11.10 because it's old and has only one purpose: Video's. After a bit of fiddling around I found a resolution that works pretty well: 720*480 pixels. The only thing is, I can't correct for overscan! TV itself has no options to do so, so I resorted to the overscan option within the Nvidia settings... it has a pretty slider thingie which supposedly let's me correct the problem... but every time I touch the slider with my mouse, the nvidia-settings windows instantly closes itself.

I ran a terminal, went root and gave "nvidia-xonfig" to make sure there is an xorg config file present (there is) but still, even when I run nvidia-settings as root, it crashed when I touch the slider. 

Where can I start looking next? It works fine and all, I just want to see my whole desktop.

---

### Post by Paddy Landau on 2011-11-29
I don't know the answer, but as no one has answered you, let me at least give you a clue where to start looking. Then maybe someone can help.

Run your Nvidia settings again, but this time don't do it from the menu. Instead, open a terminal and run it from there. When you touch the slider and the settings program crashes, you should see a bunch of error messages in your terminal. Copy-and-paste the command and its output into a post here. (Please enclose the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] otherwise it is hard to read.)

---

### Post by thinkr on 2012-01-30
I'm new to Ubuntu, so I'm unsure about posting let alone the system!

I have also experienced the same problem in Nvidia Settings as [htt-thalan]("http://ubuntuforums.org/member.php?u=938011").

On my system the TV OverScan slider is set on 8. If I try to change this the NVIDIA X Server Settings window disappears.

Here is the error message that appears in the terminal window:

```
...@HomeBuntu:~$ sudo nvidia-settings
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 255 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
...@HomeBuntu:~$ 
```

I hope this will help.

---

### Post by Paddy Landau on 2012-01-31
Whenever you run a GUI program, please use gksudo instead  of sudo, otherwise it can cause problems. So, you could also  try the following (although I doubt it would make a difference in this  case):
```
gksudo nvidia-settings
```However, I'm not familiar with nvidia-settings; are you supposed to run it as root? What happens if you run it without sudo?
```
nvidia-settings
```

---

