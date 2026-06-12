---
title: "lirc configuration on 9.04"
date: 2009-06-25
forum: Mythbuntu
---

### Post by zapstrap on 2009-06-25
I'm attempting to get lirc working in mythbuntu 9.04.  

I have a homebrew receiver connected to my serial port.

If I open the Synaptic Package Manager, it says all lirc related files are installed.
If I open the Mythbuntu Control Center, "Enable a Remote Control" was initially not checked, so I checked it and clicked apply.  It went through several steps, and I got this:


  * Reloading kernel event manager...
   ...done.
 * Stopping remote control daemon(s): LIRC
   ...fail!

Reading package lists... Done
Building dependency tree       
Reading state information... Done
 * Reloading kernel event manager...
   ...done.
 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...fail!


Every resource I've reviewed so far gets into great detail about recompiling a kernel to support this capability, but cautions that it may not be needed for newer releases.  These resources all appear to be at least two years old (all I could find so far).

Running lsmod doesn't show any installed lirc related modules of any kind.
Picking through the /dev directory shows /dev/lircd exists, but that's all.  Should there be more?

If I type "sudo /etc/init.d/lirc start" in a terminal window I get:

* Loading LIRC modules [ OK ]
* Starting remote control daemon(s) : LIRC   [fail]

Is there an up-to-date resource on how to do this somewhere?  Better yet, does anybody have any thoughts on what's gone wrong?  How to fix?

---

### Post by zapstrap on 2009-06-26
*<edit>*
I went back into the lirc setup screen within the Mythbuntu Control Centre, and just picked a remote rather than selecting *custom*.  This seems to have got the lirc devices /dev/lirc0 and /dev/lircd installed and working.  I can now see the devices, and that the lircd daemon is running.  I came back to add this because I realized everything below followed this one step.  The remote I chose from the list was a RadioShack 15-2116 (has a JP1 connector), largely because the remote I really wanted to use wasn't listed.
*<edit>*

After much fiddling about, I got a jp1 remote (URC-6011) working with a homebrew receiver.  I tried using the inbuilt tools to create an lircd.conf file with just any old device code on the remote, but they simply would not work for me.  The program crashed, and captured buttons incorrectly throughout the whole process.  I thought maybe I had somehow botched the homebrew circuit, as it was totally inconsistent.  I also used a different IR device because I couldn't find the popular TSOP1738 or TSOP1838 (used a TSOP34838 instead).  After programming the remote with a device upgrade, and copying the supplied lircd.conf file into place, all works perfectly...in mythtv.

Due to problems experienced earlier with reading DVDs I had specified the vlc player for watching movies, and mplayer for everything else.  Neither of these applications seem to respond to the remote, but mythtv works perfectly, so the hardware and at least the low-level software must be working.

After staying up far too late for a working stiff, I discovered the .lircrc files in the home directory.  This seems obvious enough, "include ~./lirc/vlc" to control the vlc player, and similar for mplayer.  Neither application responds to the remote.  After more reading, I modified the line in mythtv to launch vlc like so: vlc [misc. options] --extraintf lirc %d.  This still didn't work, but watching the debug output from vlc showed it was receiving stuff, just not anything sensible.

More reading, and I discover that in the lircrc files, blocks I would have expected to see like:

```
begin
    prog = vlc
    button = PLAY
    repeat = 3
    config = P
end
```...which more or less work in mythtv, don't work in vlc.  Why?  Because that last line: "config = P" is not what vlc wants.  What it really wants is: "config = key-play".

key-play?  OK, more reading, where is the list of key-bindings, or key messages or whatever they're called for vlc?  I have no issue creating a file to handle this, but I need the list to do it.  I don't feel like guessing when this should be documented somewhere.

Soooooo...does anybody know where this is documented?  I looked at the vlc man page (not helpful), then I looked at their suggested on-line docs and found no information on this subject.

I have the same issue with mplayer.  Much snooping yielded a message (here in these forums) with a small chunk of lircrc file for mplayer.  It looks from comparing it to the man page that the author used the remote to issue joystick control commands to mplayer.  I tried this, and got *somewhere*, but I'm really unhappy with the performance.  The program seems slow to respond and the display frequently siezes up, leaving sound running.  As with vlc, is there a golden list of config=xxxx commands for mplayer?  Something like:

```
begin
    prog = mplayer
    button = 1
    repeat = yyy
    config = seek ... ???
end
```A man page or on-line reference? Anything for vlc, mplayer or any other popular media apps?

---

### Post by zapstrap on 2009-06-27
Hmm, I'm starting to know how the lady with all the cats feels.  Just sitting around talking to myself...

Well, I hope somebody finds this a little helpful.

For vlc, the list of key commands really Really REALLY should be in the man page!!!

See [http://wiki.videolan.org/How_to_Use_Lirc](http://wiki.videolan.org/How_to_Use_Lirc) for a complete list of supported keys from vlc 0.8.6.  There is a rather cryptic one liner showing how to extract the key commands using a call to vlc and piping the output through sed...TOO FAR!  Not to harp on a point, and knowing this isn't a vlc/mplayer/lirc forum but a mythtv forum, supported keys *should* be in the man page so you know what corresponds to what you're using.  Fobbing off a user to a website that might move or be down just sucks.  It seems like there's a little too much documentation corresponding to obsolete versions, no?  It's made this process more difficult than it needed to be.  Anyway, rant over, use the key commands in the *config = key...* lines in the vlc lircrc file:

```

...
begin
    prog = vlc
    button = PLAY
    config = key-play
end
...

```Lastly (on vlc) run *vlc --extraintf lirc [other options] <filename>* and all should be well.

For mplayer, things are much more sensible.   No extra command line switches are needed when running the player.  Also, to get the list of supported commands, type this:

[I]mplayer -input cmdlist

[/I]The list of commands should be used in the *config = ...* lines in the mplayer lircrc file.  Most of the commands are not useful when mythtv launches mplayer, but it's pretty obvious which commands are important.  The mplayer lircrc file should have blocks in it that look like this:

```

...
begin
    prog = mplayer
    button = PLAY
    config = gui_play
end
...

```...for each button on the remote.

I realize each remote is different, but shouldn't the more universal buttons be configured in the lircrc file for each of the included multimedia apps in mythbuntu out of the box?  PLAY/STOP/FF/REW/PAUSE and so on should all be pretty much universal from any remote for controlling a pvr, no?  I suppose it's complicated by the fact that not everyone will use lirc to get remote commands into the box.

Hmm, if I had cats I'd go talk to them, I guess I'll settle for rambling here...No wait, now that I can use vlc or mplayer to watch stuff out of mythtv, and still control the players using the same remote, maybe it's finally time to start the movie.

---

