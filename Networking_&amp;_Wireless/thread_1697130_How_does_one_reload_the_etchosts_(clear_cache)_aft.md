---
title: "How does one reload the /etc/hosts (clear cache?) after adding a domain to 127.0.0.1"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2011-02-28
I often manually add a troublesome domain (e.g., advertisements, fake virus alerts, etc.) to my /etc/hosts file on Ubuntu 10.04 Lucid; but the effect isn't immediate.

My hosts file is already fifteen thousand lines long (having combined all the hosts files I could find on the net, including the MVP one); but I still, almost daily, find a new irritant to add to my /etc/hosts file.

My problem is I do not understand WHEN the /etc/hosts file is next read after a change.

I've been rebooting to make sure the hosts is re-read; but there must be a simpler way.

My question:
- WHEN is the /etc/hosts file reconsidered in Ubuntu?
- Is there a way to have the /etc/hosts file re-read sooner?

---

### Post by rocksockdoc on 2011-02-28
I should note that I searched and had found this:
[- ]("http://ubuntuforums.org/showpost.php?p=9437554&postcount=4")[B][How to refresh hosts file without rebooting]("http://ubuntuforums.org/showpost.php?p=9437554&postcount=4")

[/B]Which suggested:
sudo /etc/init.d/networking restart

But, that did not work.

As a test, I put the following in the /etc/hosts:
127.0.0.1  [www.ubuntuforums.org]("http://www.ubuntuforums.org")

And, then ran:
```

sudo /etc/init.d/networking restart

```[B]

And, I'm still posting here! :)
[/B]

---

### Post by rocksockdoc on 2011-03-01
Nobody knows how to reload the /etc/hosts file without rebooting?

---

### Post by chili555 on 2011-03-01
> As a test, I put the following in the /etc/hosts:
127.0.0.1 [www.ubuntuforums.org](www.ubuntuforums.org)

And, then ran:```
sudo /etc/init.d/networking restart
```
And, I'm still posting here! I'm not sure that means what you think it means. I believe this entry in /etc/hosts means that when someone requests connection to  [www.ubuntuforums.org](www.ubuntuforums.org), send them to 127.0.0.1. I think there is a strong possibility that it's a different IP address than, say [http://www.ubuntuforums.org/forumdisplay.php?f=336](http://www.ubuntuforums.org/forumdisplay.php?f=336), what I have bookmarked for Networking and Wireless.

Having any other setting except localhost associated with 127.0.0.1 is tricky business. I'd switch back at once, if I were you.

I am pretty sure changes to /etc/hosts are immediate. I am testing now.

Edit: I can only get it to re-read after a reboot. Sorry.

---

### Post by rocksockdoc on 2011-03-02
> **chili555 said:**
> I can only get it to re-read after a reboot. Sorry.

Thank you for answering. That's my experience also. A reboot "always" clears the cache and causes the modified /etc/hosts file to be read.

I guess what I need to find out is HOW and WHEN the /etc/hosts file is read under other circumstances than a complete reboot! 

I don't think the /etc/hosts file is only read once because, eventually, changes to my /etc/hosts file do seem to take place within a long session (hours).

**[SIZE=3][COLOR=DarkRed]The question is "what" triggers the /etc/hosts file to be re-read?[/COLOR][/SIZE]**

> **chili555 said:**
> Having any other setting except localhost associated with 127.0.0.1 is tricky business. I'd switch back at once, if I were you.

Modifying the /etc/hosts file is a time-honored way to eliminate noxious websites and advertisements. Proof is on the net where you can download complete hosts text files containing tens of thousands of entries, e.g., see: [Blocking                   Unwanted Parasites with a Hosts File]("http://www.mvps.org/winhelp2002/hosts.htm"). I've been using this method for more than a decade on a variety of platforms; and it works just fine. 

The only gotcha is that I don't understand when/how the Ubuntu /etc/hosts file changes take place. 

For those networking gurus out there ... the question for all is:
**Q: When is the /etc/hosts file read (and how can one force a re-read)?**

---

### Post by chili555 on 2011-03-02
> Modifying the /etc/hosts file is a time-honored way to eliminate noxious websites and advertisements.Do you think modifying the 127.0.0.1 localhost line works exactly the same way in Linux?

---

### Post by inkrypted on 2011-03-02
Try "sudo killall -hup inetd"  without the quotes which will restart the inetd process without requiring a reboot.

---

### Post by rocksockdoc on 2011-03-02
> **chili555 said:**
> Do you think modifying the 127.0.0.1 localhost line works exactly the same way in Linux?

Oh, I see your concern. 

Don't worry. Nobody ever said they were modifying the localhost line. :)

If you look at the 700 KB hosts file, containing fifteen thousand blocked domains that [millions of people use on Windows]("http://www.mvps.org/winhelp2002/hosts.htm"), you'll see what I mean:
- [hosts.txt]("http://www.mvps.org/winhelp2002/hosts.txt")

Here's just a tiny excerpt from that, the most common hosts file on the planet:
```

# This MVPS HOSTS file is a free download from:            #
# http://www.mvps.org/winhelp2002/
[COLOR=Blue] 127.0.0.1  localhost[/COLOR]
#start of lines added by WinHelp2002
... blah blah blah ... 
[COLOR=DarkRed]127.0.0.1  doubleclick.net #[McAfee.Cookie-Doubleclick]
127.0.0.1  www.visit-tracker.com
127.0.0.1  anti-virus-2009.com[/COLOR]
... blah blah blah ... 

```Interestingly my Ubuntu 10.04 (Lucid) hosts file seems to have an additional line for the hostname, which I find confusing since the hostname is already in the /etc/hostname file (so why require it in the /etc/hosts file?).
```

[COLOR=Blue]127.0.0.1       localhost.localdomain   localhost
127.0.1.1       ubuntu ubuntu[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

#start of lines added by WinHelp2002
... blah blah blah ... 
[COLOR=DarkRed]127.0.0.1  doubleclick.net #[McAfee.Cookie-Doubleclick]
127.0.0.1  www.visit-tracker.com
127.0.0.1  anti-virus-2009.com[/COLOR]
... blah blah blah ...

```So, in summary, nobody is touching the "localhost" line. 

Likewise, nobody is touching the cryptic 2nd line with the hostname repeated twice (for what reason this second line is required I don't know because it's simply a repeat of the hostname file; but in this respect, the Ubuntu format differs from the Windoze format as you suggested).

And, I left alone the default IPv6 lines (even though I don't understand them ... actually, 'because' I don't understand them).

But I do understand the purpose of the next fifteen-thousand lines! 

And that is so that I never see advertisements, so that I never see known pop-up spam, so that I never get tracked by known trackers, so that I never get known anti-virus alerts, so that known automatic-chatbots never pop up, etc.

The only lines being added are those of the unwanted parasitic hosts, known virus scams, all unwanted advertisements, all unwanted trackers, etc.

So I hope this answers your question. I'm quite confident that the fifteen-thousand line /etc/hosts file is syntactically correct.

My only questions are:
[COLOR=DarkRed]**Q: What actually causes the hosts file to be read in Ubuntu?**[/COLOR]

And, I have one bewilderment question:
**[COLOR=DarkRed]Q: Why is the hostname in the default Ubuntu hosts file when it's already required in the hostname file?[/COLOR]**

---

### Post by rocksockdoc on 2011-03-02
> **inkrypted said:**
> Try "sudo killall -hup inetd"

OK. Here is what I will try next:
0. I'll kill my firefox (which wipes out the firefox cache by default).

1. I'll add to my existing /etc/hosts file the line:
```

127.0.0.1 ubuntuforums.org

```2. I'll bring up firefox and attempt to load a new web page in the ubuntuforums domain.
And, I'll ping the same domain.
```

$ ping ubuntuforums.org
$ telnet ubuntuforums.org 80

```3. I'll then run your kind suggestion in a terminal window:
```

$ sudo killall -hup inetd

```4. I'll reattempt step 2 above after closing the firefox browser (to clear its cache).

If the ping works and the browser comes up with a 404-not found, then the loading of the updated hosts file will be confirmed.

Gimme a few minutes ...

---

### Post by rocksockdoc on 2011-03-03
The code snippet was promising:
```

$ sudo killall -hup inetd

```But something was wrong with the syntax:

```

$ sudo killall -hup inetd
Usage: killall [OPTION]... [--] NAME...
       killall -l, --list
       killall -V, --version

  -e,--exact          require exact match for very long names
  -I,--ignore-case    case insensitive process name match
  -g,--process-group  kill process group instead of process
  -y,--younger-than   kill processes younger than TIME
  -o,--older-than     kill processes older than TIME
  -i,--interactive    ask for confirmation before killing
  -l,--list           list all known signal names
  -q,--quiet          don't print complaints
  -r,--regexp         interpret NAME as an extended regular expression
  -s,--signal SIGNAL  send this signal instead of SIGTERM
  -u,--user USER      kill only process(es) running as USER
  -v,--verbose        report if the signal was successfully sent
  -V,--version        display version information
  -w,--wait           wait for processes to die

```

Then, I realized the "hup" should be "HUP"; but that simply said that inet wasn't found:
```

$ sudo killall -HUP inetd
inetd: no process found

```Trying to get the process id (PID) of inetd:
```

$ ps -elfww | grep inetd| grep -v grep

```Should reveal the process id for "inetd" but it didn't.

I need to bone up on the "ps" command as I'm relatively new to Ubuntu (having come over from Windows).

---

### Post by inkrypted on 2011-03-04
Hate to answer a question with a thread but I thought this might help or at least provide insight.
[http://ubuntuforums.org/showthread.php?t=3397](http://ubuntuforums.org/showthread.php?t=3397)
As for my command I educated myself by finding the inetd is no longer a part of Ubuntu or at least not installed. If you doing this for ad or malware blocking purposes there are many different and easier way to accomplish this. If your using Firefox, Chrome or Opera might I recommend Ad Block or Ad Sweeper.

---

### Post by rocksockdoc on 2011-03-10
> **inkrypted said:**
> If your using Firefox

This is an interesting statement from the following Linux reference:
- [URL="http://jblevins.org/log/hostname"]Linux Hostname Configuration
[/URL]
> ... the effects of changing /etc/hosts are immediate. Some applications such as Firefox seem to cache this information and may need to be restarted ... 

---

