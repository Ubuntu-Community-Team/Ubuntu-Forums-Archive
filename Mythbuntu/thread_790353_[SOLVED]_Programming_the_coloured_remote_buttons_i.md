---
title: "[SOLVED] Programming the coloured remote buttons in 8.04"
date: 2008-05-11
forum: Mythbuntu
---

### Post by freymann on 2008-05-11
I had configured everything quite nicely on my living-room 7.10 mythbuntu machine, but after upgrading to 8.04 I've now lost some custom functions I had assigned to the Red, Green, Yellow and Blue buttons on my remote.

Here's what I had done with 7.10:

[http://ubuntuforums.org/showthread.php?p=4733977#post4733977]("http://ubuntuforums.org/showthread.php?p=4733977#post4733977")

I see that 8.04 now uses a ~/.lirc directory with includes.

So I added my code for the 4 colored buttons to the top of 

~/.lirc/mythtv

and restarted lirc with

sudo /etc/init.d/lirc restart

but nothing happens anymore :-(

A sample command is:

begin
    remote = mceusb
    prog = irexec
    button = Green
    config = /home/freymann/.mythtv/x10lights aon &
end


 where here, when I press the green button on the remote, I want it to execute "/home/freymann/.mythtv/x10lights aon" like it used to under 7.10

 If I run 'irw' and press the colored buttons, I see the correct identification on screen.

 I would also like to be able to program the Power, LiveTV, RecTV and DVD buttons on my other 2 remotes to do the same thing as the colored buttons (those remotes are gray/silver in color and don't have the colored buttons at the bottom). I had tried that with 7.10 and had the same results as I'm having now in 8.04 with the colored buttons.

 Any suggestions?

---

### Post by amphibem on 2008-05-11
Im pretty sure the file you need to modify is ~/.mythtv/lircrc

Thats what it is for me.

---

### Post by freymann on 2008-05-11
> **amphibem said:**
> Im pretty sure the file you need to modify is ~/.mythtv/lircrc

Thats what it is for me.

Yes, but in mythbuntu 8.04

~/.mythtv/lircrc

is now symlinked to

 ../.lirc/mythtv

So it's the same file, and when I look at that file it has the info for the 4 colors at the very top.

Is there something else I need to restart in order for the changes to take effect? I was out of mythfrontend, working in terminal, made the change to the lircrc file, did a sudo /etc/init.d/lirc restart, and then went back into mythfrontend... The remote works but the colored buttons don't do anything.

---

### Post by Nikas on 2008-05-11
My irexec-commands did not work with 8.04.
They worked in 7.10.

The problem is irexec. You need to run irexec manually.

# irexec 
or
# irexec your-path-to-lircrc

(i use irexec /home/niklas2/.mythtv/lircrc)
Look at the output when pressing your buttons.
If you can get it to work, add irexec -d your-path-to-lircrc to rc.local or whatever that makes irexec start with the computer.
-d or --daemon = run in background.

I dont know if it will work.

[http://www.lirc.org/html/irexec.html](http://www.lirc.org/html/irexec.html)

---

### Post by bredington on 2008-05-11
Just installed (clean format, losing 7.10).  Could someone PLEASE just tell me which remote I need to select in the installer?  8.04 provides choices:
Hauppauge DVB-s card (ver, 2.1)
Hauppauge HVR-1100
Hauppauge HVR-1300
Hauppauge Nova-T 500
Hauppauge TV card

I have a 250 and a 150, both came with the same remote, gray with 4 colored buttons on the bottom.  There is no number on it anywhere that indicates what selection I should make at this screen.  I spent most of a year with 7.10 and never did get the remote to work.  Why after all this time is this still so fringe?

Any help is greatly appreciated.

---

### Post by Nikas on 2008-05-11
> **bredington said:**
> Just installed (clean format, losing 7.10).  Could someone PLEASE just tell me which remote I need to select in the installer?  8.04 provides choices:
Hauppauge DVB-s card (ver, 2.1)
Hauppauge HVR-1100
Hauppauge HVR-1300
Hauppauge Nova-T 500
Hauppauge TV card

I have a 250 and a 150, both came with the same remote, gray with 4 colored buttons on the bottom.  There is no number on it anywhere that indicates what selection I should make at this screen.  I spent most of a year with 7.10 and never did get the remote to work.  Why after all this time is this still so fringe?

Any help is greatly appreciated.

Try them all. ;)

[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-250](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-250)
[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-150](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-150)

The remote looks exacly like mine. I have two Nova T-500 in my server so try that one.

---

### Post by freymann on 2008-05-11
> **bredington said:**
> Just installed (clean format, losing 7.10).  Could someone PLEASE just tell me which remote I need to select in the installer?  8.04 provides choices:
Hauppauge DVB-s card (ver, 2.1)
Hauppauge HVR-1100
Hauppauge HVR-1300
Hauppauge Nova-T 500
Hauppauge TV card


 I have a Hauppauge 150 but I selected Microsoft (Philips, new et al) as my remote.

 The transmitter selection is new I think in 8.04? I left that one blank and everything is working for me, including changing channels on my stb (with some config changes I did for 7.10 included)

---

### Post by freymann on 2008-05-11
> **Nikas said:**
> My irexec-commands did not work with 8.04.
They worked in 7.10.

The problem is irexec. You need to run irexec manually.

# irexec 
or
# irexec your-path-to-lircrc

(i use irexec -d /home/niklas2/.mythtv/lircrc)


 Beauty! 

 This worked like a charm! Thanks!!

---

