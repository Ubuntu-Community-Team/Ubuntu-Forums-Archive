---
title: "The quarterly &quot;fuppes broke itself again&quot; thread"
date: 2010-04-19
forum: Multimedia Software
---

### Post by s1500 on 2010-04-19
It has come to that time again, kids. The flowers are blooming, the snow is gone, and fuppes has now randomly decided to stop working.

I did my best(with a grian of salt here) to upgrade from the 440 to 660 build, or whichever the latest build is. I did the usual 'make install', with it giving me about 200 pages of technobabble, but not really telling me what installed to where. *sigh*

Anyways, I attempted to do my best to clean out all old traces of fuppes, including hidden folders(why?), but keeping my config files. I do not like how when fuppes gives you "cannot bind to socket", the process still runs. 

The latest symptom is that I try to connect to it via my Xbox to play some tunes, and it instantly goes back to the dashboard, when it should be playing a randomly-chosen mp3.

How do I fix this? I beg the mercy of the court. I'm on 9.10. When I do ask kindly, do not link to other threads that link to other threads, ad infintum. Let us begin a fresh page.

---

### Post by Shhnap on 2010-05-07
That's not good. It sounds like you are pretty frustrated and we do not want that at all. Here are your problems as far as I can see them:

[LIST=1]
[*]I do not like how when fuppes gives you "cannot bind to socket", the process still runs.
[*]I try to connect to it via my Xbox to play some tunes, and it instantly goes back to the dashboard, when it should be playing a randomly-chosen mp3
[/LIST]

They are two bugs that we can take a look at. The first one is caused by an error thrown in the socket code. I should go around and make the code more robust by adding in catches to the errors that are thrown.

The second is unknown behavior to me and I would have to test it out and see what is causing it. But that the problem is that your setup is your setup and in order to replicate it I would need the same audio files in the same directory and the same configuration. It is better if you can give me any error messages that may appear with fuppes being annoying and give me pointers to work with. Very soon I plan on writing a tracer, so that you can press a button on fuppes to start tracing all messages sent and then do something that shows the problem and then stop it and send me the result. That way we can see exactly what went wrong.

For now I am happy to help solve the problems that you may be having.

---

### Post by s1500 on 2010-05-07
That's the weird thing. When I go into fuppes, not fuppesd, none of the key commands(rebuild, etc) don't do anything. No response, nothing.

When I get free time, I'm going to look into alternatives. wikipedia lists many different UPNP setups for Linux. I tried a few others to no avail, but others are new to me. 

There's a point where I just want it to work & want to take the path of least resistance. When it comes to playing MP3s, etc from Linux to the Xbox, that's the first thing that comes to mind.

Sad watching Fuppes in its earlier version sputter and eventually completely fail. I had to restart it several times, then every time I fired up the 360, then nothing. I wish free open source software worked better.

---

### Post by s1500 on 2010-05-10
Found something strange last night. I have no vfolder.cfg. Trying to go into the interactive mode(ie fuppes instead of fuppesd) does nothing when I hit V(rebuild virt. folder). What would cause this?

I also tried rhythmbox's UPNP sharing plugin. Nothing shows up for it.

---

### Post by Shhnap on 2010-05-10
Sorry for the slow response. I am not sure about the vfolder.cfg disappearing but I can assure you that there are no file remove syscalls in Fuppes. Therefore if you had a vfolder.cfg and now it is gone then it was not Fuppes that removed it. That is quite odd, I recommend getting a new one from the Fuppes Sourceforge Repository. Fuppes will not work for the XBox without the VFolder configuration file.

Also the non-responsive keys is something that does not happen on the latest development version (not the svn one). So maybe with the next SVN release something will be fixed.

In the meantime we are hard at work on many changes. If you want to test that the features work on the latest one then I could let you?

---

### Post by s1500 on 2010-05-12
So what's the link to download the latest build? I'll give 'er a try.

---

### Post by Shhnap on 2010-05-12
I have PM'd you the link as I want to keep public hits on my server low for now. Anybody that reads this can ask me for the link but I want to keep access by approval for now.

(However I would rather just host it on github and that would remove this problem among others; the fuppes developers are discussing our options)

---

### Post by s1500 on 2010-05-18
Looks like it might be somewhat my fault.I wasn't running 9.10. Thought I had 9.10 installed, but I guess not. 

Most likely I shied away from upgrading to 9.10 since I know before fuppes didn't like distro upgrades at all, and quickly broke once the deed was done.

So, I'm going to finish the 9.10 install(I've been going back & forth on it on all the prompts it does) & going to give fuppes another try.

---

### Post by s1500 on 2010-05-22
Something really strange and unexplained happened between my 360 + Linux server. 

I tried this program called ushare and, I'm almost at a loss for words... It's doing this strange thing to my Xbox. It's actually playing music through it! 

Not only that, I threw all 5K files at it, and it was even able to list the artists!

At a loss for words here!

Rhythmbox now shows up, but as expected, "loses connection". Ushare is actually working!

I'll just stick with this then since my xp laptop downstairs is randomly failing.

---

