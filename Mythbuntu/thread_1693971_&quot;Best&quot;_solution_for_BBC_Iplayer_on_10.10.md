---
title: "&quot;Best&quot; solution for BBC Iplayer on 10.10"
date: 2011-02-23
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-02-23
hey guys, pretty much as per the title really, what is the best way for me to get the BBC Iplayer / ITV and 4OD working from within the Myth frontend?  

I used to use mythvodka but it was pretty ropey if im honest and I was hoping there might be a mythstream type solution?

Thanks.

---

### Post by lastdeadmouse on 2011-02-24
Maybe not exactly a mythstream solution, but this is how i've done it.  Setup tor and vidala, and in tor's conf file you can define an endpoint of gb. Read their documentation for more info. Then an extension for firefox called foxyproxy allows you to use the tor network for specific adressess like bbc.co.uk. Traffic to bbc will pop out of gb, but the nice thing is it will actually stream the video directly. Then just setup firefox as your mythbrowser or add a custom menu link for it.  This is all based off of a few different walkthroughs and some additional massaging. Mostly based off of hurwi.net/blog/?p=28.
Sorry if im not entirely clear, but im typing on my phone.

Edit:fixing an android spellcheck :-)

---

### Post by geekyhawkes on 2011-02-25
Thanks for the reply, seems pretty long winded way of getting iplayer working.  Not taking anything away from what you have done, but if im launching a browser why not just point it to bbc.co.uk/iplayer?

---

### Post by Cuppa-Chino on 2011-02-27
hi, I just use mythnetvision plugin for iplayer, if you are using a recent mythbuntu and the 0.24 mythtv then that should work, (be warned it takes a while to download the structure of the iplayer available files..., I aborted like 3 times thinking it was broken before just letting it run for a while)

---

### Post by Lem on 2011-02-28
I currently have both xbmc and myth running as the iplayer in xbmc is vastly superior to netvision.

---

### Post by jim.hitch on 2011-03-01
I'm in the middle of setting up mythtv for the first time and want to include both skype and iplayer in it.

For me mythnetvision keeps freezing when I try to come out of it, so I've been looking for how to have a menu option that would take me out of mythtv and then hopefully put me back in again.

I have found this solution for [Skype]("http://blog.alessiosignorini.com/2010/07/how-to-integrate-skype-and-mythtv/"), which I haven't had a chance to try yet. I can't see why it wouldn't also work for iPlayer.

I'll have a go over the next couple of days and post the outcome here.

Jim

---

### Post by geekyhawkes on 2011-03-10
I like the sound of the iplayer grabber for mythnetstream but when i follow this i dont have the option to subscribe;

[http://www.mythtv.org/wiki/Bbciplayer.py](http://www.mythtv.org/wiki/Bbciplayer.py)

Im guessing its because i dont have the bbciplayer.py python script, any chance someone could upload it for me and tell me where it should be placed?  

Thanks.

---

