---
title: "rubyripper crashes -- why?"
date: 2008-12-01
forum: Multimedia Software
---

### Post by le_vainqueur on 2008-12-01
I just installed rubyripper because I heard it is easy to use to rip VBR mp3 files.  Upon trying to rip a CD, it crashes on track #6 with the following error in the terminal I ran it from

> Ripping track 6
Adding track 6 (mp3) into the waitingroom..
Inside handleThreads: maxthreads = 0, threads = 0
/usr/lib/site_ruby/1.8/rr_lib.rb:1296:in `conv': "\342\200\231s Room)\" --ta"... (Iconv::IllegalSequence)
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1296:in `mp3'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1243:in `doMp3'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1114:in `encodeTrack'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1101:in `handleThreads'
	from /usr/lib/ruby/1.8/monitor.rb:242:in `synchronize'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1094:in `handleThreads'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1090:in `addTrack'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:874:in `ripTracks'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:862:in `each'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:862:in `ripTracks'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:856:in `initialize'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1348:in `new'
	from /usr/lib/site_ruby/1.8/rr_lib.rb:1348:in `start_rip'
	from /usr/bin/rrip_gui:233:in `do_rip'
	from /usr/bin/rrip_gui:229:in `initialize'
	from /usr/bin/rrip_gui:229:in `new'
	from /usr/bin/rrip_gui:229:in `do_rip'
	from /usr/bin/rrip_gui:222:in `start_rip'
	from /usr/bin/rrip_gui:88:in `create_signals'
	from /usr/bin/rrip_gui:1118:in `call'
	from /usr/bin/rrip_gui:1118:in `main'
	from /usr/bin/rrip_gui:1118


What does this message mean, and why is the program crashing?

---

### Post by MonkeeSage on 2008-12-03
> **le_vainqueur said:**
> I just installed rubyripper because I heard it is easy to use to rip VBR mp3 files.  Upon trying to rip a CD, it crashes on track #6 with the following error in the terminal I ran it from

...

What does this message mean, and why is the program crashing?

It means that iconv is failing to convert the unicode character "’" (\342\200\231 in octal, or \xe2\x80\x99 in hex), the exception is uncaught, and the program dies with the traceback you posted. I've submitted a bug report for this ([here](http://code.google.com/p/rubyripper/issues/detail?id=259)) and a patch.

To try the patch:

1.) Download [the patch file](http://rubyripper.googlecode.com/issues/attachment?aid=-8800324185748229906&name=fix_UTF8_quotes_in_tags.diff).
2.) cd /usr/lib/site_ruby/1.8
3.) sudo patch -p0 -i /path/where/you/downloaded/fix_UTF8_quotes_in_tags.diff

Then try ripping again and see if it works.

---

### Post by MonkeeSage on 2008-12-11
> **MonkeeSage said:**
> It means that iconv is failing to convert the unicode character "’" (\342\200\231 in octal, or \xe2\x80\x99 in hex), the exception is uncaught, and the program dies with the traceback you posted. I've submitted a bug report for this ([here](http://code.google.com/p/rubyripper/issues/detail?id=259)) and a patch.

To try the patch:

1.) Download [the patch file](http://rubyripper.googlecode.com/issues/attachment?aid=-8800324185748229906&name=fix_UTF8_quotes_in_tags.diff).
2.) cd /usr/lib/site_ruby/1.8
3.) sudo patch -p0 -i /path/where/you/downloaded/fix_UTF8_quotes_in_tags.diff

Then try ripping again and see if it works.

Patch is [merged upstream](http://code.google.com/p/rubyripper/issues/detail?id=259&can=1&q=id3&colspec=ID%20Type%20Status%20Summary%20Stars%20Opened%20Modified#c3)

---

