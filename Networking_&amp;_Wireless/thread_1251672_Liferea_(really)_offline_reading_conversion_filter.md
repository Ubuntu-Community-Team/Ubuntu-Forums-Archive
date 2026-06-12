---
title: "Liferea (really) offline reading conversion filter script"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by bornagainpenguin on 2009-08-27
Has anyone had any success with this?  I gave it a try and it seems to break something or another, the same feeds that will update automatically without the filter die a horrible death and the app is convinced the feeds aren't even valid!  O_o;  SO has anyone managed to get this to work for them?

[http://pigeond.net/blog/2009/07/03/liferea-really-offline-reading-conversion-filter-script/](http://pigeond.net/blog/2009/07/03/liferea-really-offline-reading-conversion-filter-script/)

> **Pigeond]So, I'm not the only one looking a solution for [this problem](http://ubuntuforums.org/showthread.php?t=539437).

Basically I want my RSS reader to fetch things (images for example) needed to display every entry during updates, so I can read them offline. Images in most feed entries are referenced remotely ([http://)](http://)), which are usually not downloaded until the entry is actually viewed. Some feeds use enclosures but that works more like an attachment rather than for content.

I've tried quite a few RSS readers and [Straw](http://projects.gnome.org/straw/) seems to be the only one that does full automatic image fetch during updates. However Straw's development has been [stalling](http://strawreader.wordpress.com/2009/06/14/update/), and the latest version seems to be quite unstable.

Liferea has been my RSS reader for quite a while, and so I've decided to do it myself with (hopefully) the simplest way possible: a Liferea conversion filter which parses a feed and fetches things for offline reading.

At the moment it works by looking for <img> tags and fetches the image using **wget**, and then replaces the original image src to point to the local one.

It's a pretty simple perl script. I have written it in a way so it can be extended it to parse and fetch other things in the future, maybe embedded videos for example. It currently downloads all images, one by one. It also checks if a file is already downloaded or not. You can change <code>$SAVE_PATH</code> in the script as needed.

You can git (yes, git) the script at ```
git://pigeond.net/offline_filter.git
```. Or alternatively get the latest version [url=http://pigeond.net/git/?p=offline_filter.git said:**
> here[/url], or browse the repo at [http://pigeond.net/git/?p=offline_filter.git]http://pigeond.net/git/?p=offline_filter.git]().

To use it, set the script as the conversion filter for the feed you want to have things downloaded and it should just work.

Now I can read all the really important stuff on the train, like [xkcd](http://xkcd.com/) and [failblog](http://failblog.org/) ;).

So has anyone else tried this or had any success with it?  I gave it a shot on Hardy and like I said it just seems to break everything on me.  I hope it turns out to be something silly and obvious (read easy to fix) that I'm doing wrong...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-08-29
/BUMPing from page 8 to page 1

Also, if a moderator knows of a section more appropriate for this topic, feel free to move it there!

--bornagainpenguin

---

### Post by randName on 2009-08-30
I tried that filter on my Liferea 1.6.0 on Jaunty, unfortunately it did not work, just like how you mentioned. Only after I disabled it for a while did the feed start to function normally.

soz, another bump.

(I was randomly searching "Liferea" on Google and stumbled over this. Don't ask me why I was searching. Could be boredom from lack of development but nevermind.)

---

### Post by bornagainpenguin on 2009-08-31
> **randName said:**
> I tried that filter on my Liferea 1.6.0 on Jaunty, unfortunately it did not work, just like how you mentioned. Only after I disabled it for a while did the feed start to function normally.

soz, another bump.

(I was randomly searching "Liferea" on Google and stumbled over this. Don't ask me why I was searching. Could be boredom from lack of development but nevermind.)

Thanks for the bump!  I'll take whatever help I can get, and knowing that someone else has tried the script and had the same issues helps me by showing me it isn't neccessarily my machine at fault or my setup.  I've since emailed the guy and hopefully he'll be able to help us out!

--bornagainpenguin

---

### Post by randName on 2009-09-01
A while ago, I was trying to use Yahoo Pipes to change the images to be enclosures of a feed and changing the img src to be a local destination (e.g "file:///[homedir]/.liferea_1.6/cache/"), but it turned out to be a failure. Perhaps someone else could build on the idea?

---

### Post by bornagainpenguin on 2009-09-05
Interesting idea randName, I wouldn't know how to go about setting anything like that up though.

I emailed the guy from his blog and he doesn't seem to understand the issues at all.  I guess this was a bust, since if even the guy who wrote the script is clueless...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-10-20
Anyone manage to make this work yet?

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-10-29
/Bumping because BUMP

Anyone manage to get this to work for them yet?

--bornagainpenguin

---

### Post by pigeond on 2009-11-05
Hi bornagainpenguin,

    I've made some changes to the script. Do you want to get the latest one and try again?

    I've tested the one feed you've mentioned on my blog and it works for me here too.

    Thanks.


Pigeon.

---

### Post by bornagainpenguin on 2010-01-02
> **pigeond said:**
> Hi bornagainpenguin,

    I've made some changes to the script. Do you want to get the latest one and try again?

    I've tested the one feed you've mentioned on my blog and it works for me here too.

    Thanks.


Pigeon.

I gave it another try with the new filter you mentioned.  Still giving me the error codes..  Maybe you could make a HOWTO explaining how you set your filter so I can see what you're doing differently?  Right now it isn't working for me period.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-03-11
/hope springs eternal BUMP

---

### Post by bornagainpenguin on 2010-03-17
This is your regularly scheduled bump.  Feel free to ignore--everyone else does more or less.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-04-11
Anyone ever have any success with this?

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-03
Monthly /BUMP...you may wish to collect them all...

---

### Post by singlevalley on 2010-05-19
Hey, just to let you know that I have ben able to get liferea working offline...  Ubuntu lucid ...install liferea, and download the offline_filter.pl file into its own directory, set the execute permission, set a download directory in that script (and create it), add that script as a conversion filter,  and BAM... I get images downloaded , which is what I am interested in for now.  Send me a PM if you would like a copy of the script file..

---

### Post by bornagainpenguin on 2010-07-26
I gave up on this and installed [Naufrago!]("http://www.gnomefiles.com/app.php/Naufrago!") which does what I'd hoped to use Liferea for.

--bornagainpenguin

---

