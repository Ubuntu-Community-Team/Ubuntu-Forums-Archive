---
title: "I want to create my own Internet Talk show: I know nothing"
date: 2010-10-12
forum: Multimedia Software
---

### Post by kwabena39 on 2010-10-12
Hi, I would like to start a streaming audio/talk radio show where I can play music during breaks, talk most of the time about current events, and MAYBE even take callers.
I am now using Blogtalkradio, but the streaming and archiving quality os so terrible that I want to move up into creating my own talk show network.

I'm using Ubuntu 10.04, 64 bit

This is a good example of what I would like to do: The Global Reality Show...the guy uses Sam Broadcaster and pays a "stream bill" due every month, and you can download archives from a server linked to his website or click the application buttons for ways to get his stream:
[[URL="http://www.theglobalreality.com/radio-show"]http://www.theglobalreality.com/ra]("http://www.theglobalreality.com/radio-show")dio-show[/URL]

Please go to his website to check out what I mean...

Now I heard of this thing called IDJC, which I have installed, but I do not have the faintest idea of how to use it, let alone get jackd running properly.  It just complains and stops.  Nor have I EVER used Sam Broadcaster or anything like it.  When it comes to this thing, I'm a complete newbie. Other people on other forums say you can use Shoutcast and VLC and bypass Jackd and IDJC completely.  

Does anybody have any ideas?  Can someone provide links to tutorials out there on how to set up your own internet radio station in Linux?  I understand its alot more complicated than windows.

Thanks

---

### Post by cchhrriiss121212 on 2010-10-12
I don't know about hosting radio shows, but I could help you setup jackd. I just had a play around with idjc and it seems like a good piece of software. Please post what you get in the jack message window.

I'd imagine you'd also need your own website to host the content, or find a service for that.

---

### Post by StephenF on 2010-10-15
[http://idjc.sourceforge.net/install_first_run.html](http://idjc.sourceforge.net/install_first_run.html)

and 

[http://idjc.sourceforge.net/tutorials_shoutcast.html](http://idjc.sourceforge.net/tutorials_shoutcast.html)

---

### Post by kwabena39 on 2010-10-16
Thank you, all, for your help.  Thank you especially, StephenF, for posting those two links.  I followed them and they were helpful.  I'm still not there yet, but I got one issue resolved: the setting up of Jackd to work.  It did not quite work out the first time when I tried to follow the instructions on the IDJC page for setting up jackd.  There were some additional issues, like having to get permissions to change /etc/security/limts.conf.

Hey,  found something confusing: one of the Ubuntu pages says that after 9.10, you no longer change audio stuff in /etc/security/limits.conf, but this NEW file called:  /etc/security/limits.d/limits.conf or something like that.   But when I went to the /etc/security/limits.d folder, there was nothing in it.  Apparently, I guess the developers changed their minds and went back to the original: /etc/security/limits.conf ?

Anyway, I had to install additional software like the medibuntu repository to get ubuntu studio stuff (But I did not install the RT kernel)

Actually, I cannot install the RT kernel, because it has issues with some ATI and nVidia cards, but I did a workaround, where you "halfway" install the ubuntu studio kernel by installing a bunch of stuff into your standard ubuntu kernel.

After going to a bunch of forums, and tinkering around, I finally got jackd to run, i think.


So I'm halfway there.  Now, I am going to start to research shoutcast and how to work with IDJC.

Again, thanks for your help, and if i have any additional problems along the way, I will post them

---

### Post by kwabena39 on 2010-10-18
Question:  I followed the shoutcast link, downloaded the shoutcast software, and read the READ ME file.  I noticed that there are lot of requirements in memory and my space/cable modem is just not going to do it.  It said:

> If you don't have some/any of the above, you can still broadcast a station, 

but you'll have to pay someone for the privelege of hosting a SHOUTcast server

for you, and you won't need this piece of software.  To find good providers,

visit the SHOUTcast forums on [www.shoutcast.com](www.shoutcast.com) and hear what others say

about the growing number of streaming audio providers.


I just don't have enough to set up a server on my machine.  No...What I wanted to do was create a stream AND THEN SEND IT TO A STREAMING PROVIDER like Texas Teamspeak or some other company.  Do I need the Shoutcast stuff to do this?  How do I send my IDJC output to a streaming provider?  I cannot find any documentation on this.

Thank you

---

### Post by StephenF on 2010-10-18
> **kwabena39 said:**
> How do I send my IDJC output to a streaming provider?  I cannot find any documentation on this.
It's the same as sending it to a local Shoutcast server except instead of putting localhost as the hostname you set the external IP address and port number which will be made known to you.

Teamspeak is not Shoutcast. Find a Shoutcast provider.

Edit: I think you underestimate your streaming capability. Take your upload speed divide it by 2 then divide it by the number of listeners and that's your recommended bitrate. Most stations are averaging just 5 listeners. If you have 256kbps up then 128/5 = 25.6. Take that up to 32kbps.

---

### Post by kwabena39 on 2010-10-18
The radio broadcaster I mentioned above (Josh) streams at 128k.  That's what I want

Blogtalk is 16 k, and it sounds like ****...I mean, half the time you can't even hear what they're saying.  32 is just twice that, which isn't going to be that good.  I want at least 64k or 128,

Thank you for your clarification and help though.  That information is of big help.  Thanks again -___-

---

### Post by StephenF on 2010-10-18
Using their server you only need 256k upload speed.

---

### Post by kwabena39 on 2010-10-21
Before I get a streaming provider, I decided to do a check with my Shoutcast that I installed just to see how this is done.  I'm having some problems, and I am confused.  I got Jackd up and working, and Internet DJ console, but I CANNOT follow the instructions given in the tutorial above, because the IDJC in the Ubuntu repositories seems to be different than the IDJC talked about in the tutorial (see screenshots below)  "Output" button?  There is no Output button, instead there is a "Server button"
[IMG]http://img263.imageshack.us/img263/6550/screenshot1an.jpg[/IMG]

[IMG]http://img440.imageshack.us/img440/3005/screenshot2xi.jpg[/IMG]

and Shoutcast Master becomes grayed out when I add it...Instead, all I can see is Shoutcast/Stats Relay...Can I stream with this?
[IMG]http://img801.imageshack.us/i/screenshot3ij.png/[/IMG]

I don't even know if I am streaming or not...the button certainly does not stay darkened, or "pushed down"  There are no error messages or anything.  What is going on?  Do I have an old IDJC?  I tried to install the latest version, but ran into problems...I can't seem to get it to ./configure and make in the folders where you build the downloaded source code.

---

### Post by kwabena39 on 2010-10-21
I can't seem to be able to install the newest, IDJC-0.8.4, which, it seems, the version from my repository (Ubunto 10.04) is an outdated (broken) version [I cannot connect to a stream, not even local host...It just WON'T connect]

When I do the git command, and then go to the idjc folder inside of idjc-0.8.4, env-up spits out errors.

Then, ./configure CFLAGS="O2" spits out: "configure is not a file or directory" or something like that.

So when I drop back to /home/usrname/Downloads/idjc-0.8.4, it seems to compile, but there are some errors.

Then, when I go to make, it seems to make (puts out a long series of lines)

but then...make install...still no idjc.

There seems to be this confusion between $idjc-0.8.4 and $idjc-0.8.4/idjc.  I followed all the instructions at this site:
[http://idjc.sourceforge.net/install_build.html]("http://idjc.sourceforge.net/install_build.html")

Still no working, up to date idjc.  I installed all the dependencies and everything. Is here still a way I can get the official repository one working?  Is there something I'm missing?

Your help would be greatly appreciated.  Thanks

---

### Post by Rowanmf on 2010-10-24
please can i get some help , I have been following all the comments and how to's to get my internet radio working , when i first installed IDJC on wednesday it ran with no problems but i could not get streaming as i had not run sc_serv properly , so today when i have got sc_serv and jack running properly , IDJC does not want to run , starting from the console it gives the following :


rowan@rowan-desktop:~$ idjc
Compromise language match found en_GB
Internet DJ Console Version 0.8.3
Copyright 2005-2010 Stephen Fairchild
Released under the GNU General Public License V2.0

Language translation: en_GB
shout_initialiser: shout_init called
started 6 encoders, 6 streamers, 2 recorders
threads initialised
jack sample rate is 44100
failed to open serverdata file
Failed to read playerdefaults file
Restoring previous session
Traceback (most recent call last):
  File "/usr/lib/python2.6/runpy.py", line 122, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/lib/python2.6/runpy.py", line 34, in _run_code
    exec code in run_globals
  File "/usr/lib/python2.6/dist-packages/idjcgui.py", line 3136, in <module>
    sys.exit(main())
  File "/usr/share/pyshared/idjc/IDJCfree.py", line 96, in newf
    r = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/idjcgui.py", line 3120, in main
    run_instance = MainWindow()
  File "/usr/lib/python2.6/dist-packages/idjcgui.py", line 3047, in __init__
    self.restore_session()
  File "/usr/lib/python2.6/dist-packages/idjcgui.py", line 1534, in restore_session
    stat = os.stat(self.session_filename + "_tracks")
OSError: [Errno 2] No such file or directory: '/home/rowan/.idjc/profiles/default/main_session_tracks'
threads_shutdown commencing
rowan@rowan-desktop:~$ Mixer module has closed
threads_shutdown finished

i have tried un installing and re installing but i am getting the same .
if anybody has a few pointers i would be most gratefull .

Thanks
Rowan

Stephen Fairchild responded :


Somehow a that file got deleted from the IDJC application data directory.

In a console:
$ touch ~/.idjc/main_session_tracks

Or just wipe the ~/.idjc directory if you have further problems.

---

