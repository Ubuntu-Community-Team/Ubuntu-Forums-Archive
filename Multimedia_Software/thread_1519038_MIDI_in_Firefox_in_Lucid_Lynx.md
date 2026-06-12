---
title: "MIDI in Firefox in Lucid Lynx"
date: 2010-06-27
forum: Multimedia Software
---

### Post by Anal on 2010-06-27
Hello all.

In short: I can't play MIDI in Firefox, and I would really love to (to enjoy this site: [http://drawthedots.com/](http://drawthedots.com/) - to write music in ABC notation and listen to it in real time).

I found other (pretty older) posts about this issue and the suggested solution was to use the mozplugger plug-in while deleting the "pluginreg.dat" in the .mozilla folder before restarting the browser.

Unfortunately that didn't worked for me and neither VLC plugin or gecko plugin worked.

Is there a way to listen to MIDI in websites in Lucid Lynx and how to do it?

Thank you very much everybody!

---

### Post by lovinglinux on 2010-06-27
[http://ubuntuforums.org/showpost.php?p=8913760&postcount=4](http://ubuntuforums.org/showpost.php?p=8913760&postcount=4)

---

### Post by Anal on 2010-06-28
I did followed those instructions already, as I wrote: I did use mozplugger, but it does not work in Lucid Lynx, at least not for me. That post is about Ubuntu 9.04 (Jaunty). (Yes Timidity is installed too)


Is there anybody getting it working on the latest Ubuntu?

Thanks so much.

---

### Post by lovinglinux on 2010-06-28
> **Anal said:**
> Is there anybody getting it working on the latest Ubuntu?

I don't think will be easy to find someone who still use midi. I never used on Ubuntu, only on my old days of Windows XP.

---

### Post by Anal on 2010-06-28
> **lovinglinux said:**
> I don't think will be easy to find someone who still use midi.

Well, musicians and players!

It's still pretty widely used among them.
Here's a sample page: 

[B][http://folktunefinder.com/dosearch/?title=smarlon](http://folktunefinder.com/dosearch/?title=smarlon)
[/B]
so to get an idea about what I need. I just tried it on IE and it works. But I don't want to install windows at home just for that!

:-(

Thanks

---

### Post by cchhrriiss121212 on 2010-06-28
Musicians will be using a midi editor like Rosegarden as opposed to using a web browser. Here's a thread which has a link to a good tutorial for using audacious:
[http://ubuntuforums.org/showthread.php?t=1512561](http://ubuntuforums.org/showthread.php?t=1512561)

---

### Post by Anal on 2010-06-28
It looks like you don't know very well what you are talking about, unfortunately.

FOLK musicians use extensively ABC notation (please see [http://abcnotation.com/](http://abcnotation.com/) ), which is easily converted into MIDI.

There are plenty of websites which do that, so that most musicians just use those resources rather than installing tools on their computer.

Among those resources, there are some which uses MIDI in-line.

Actually I can't understand why I asked how to play MIDI in a browser (which is by far more than legitimate) and I get answers like "nobody uses it".

**I** do, and many others with me. Statistically, most of them use Windows so they just don't have my issues. 

If somebody could please provide a real help, I would be very thankful. 

Ciao,

---

### Post by cchhrriiss121212 on 2010-06-28
I apologise if I sounded rude, but when I think of MIDI I think of MIDI capable editors, which are also used quite extensively among musicians (I am not well versed in the folk music scene or abc notation). 

I know the solution I offered of using an external audio player was not what you specifically asked for, but I only suggested it as the other suggested method had not worked for you. It seems to me that it would do the job for you just as well, albeit a little bit differently.

Tips for the forum:
When you do not get the exact answers or help you are looking for, try not to take it personally. Remember that the people posting here are volunteers, and some of them (like me) will not always know exactly what they are talking about. 
There are also going to be many situations where Ubuntu will not give you the same functionality as Windows, but with a little patience and a little tweaking you can usually end up with an alternative. If you don't want an alternative then just stick with Windows.

Good luck with the MIDI
Chris

---

### Post by Anal on 2010-06-29
Thank you for your apologies. You are perfectly right about the fact that everybody here just volunteer; so I don't deserve anything: sorry if I took it personally then. 

I probably was very frustrated (and actually still am, darn!) because I can't solve that ******** issue!

I'm still open to any suggestion. 

Thanks! :)

---

### Post by landgrvi on 2010-07-28
Hello Anal,

I had the same problem on a fresh install of Lucid.  As far as I could tell, mozplugger wasn't successfully invoking timidity, but I couldn't find out what was failing.

I eventually tried the instructions in this article in PCLinuxOS Magazine from 2008: [http://pclosmag.com/html/Issues/200802/page01.html](http://pclosmag.com/html/Issues/200802/page01.html)

The summary: edit your /etc/mozpluggerrc and take the -Od argument out of the timidity line.  For example, you would change 'controls noisy stream: timidity -Od "$file"' to 'controls noisy stream: timidity "$file"'.

That article talks about 4 mozpluggerrc files, but I only have one, which is probably true for you too.

I didn't think such an old article would apply but it did.

Hope this helps!

---

### Post by zapaces on 2011-08-19
That last solution indeed worked! I wonder what does -Os mean...
Cheers.

---

