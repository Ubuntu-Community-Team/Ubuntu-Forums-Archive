---
title: "Sync Mythbuntu wuth Miro?"
date: 2008-10-11
forum: Mythbuntu
---

### Post by orduek on 2008-10-11
I checked and chekcked, does anyone uses Mythtv and Miro?
I wonder how to make it work.
Miro has some nice Podcast channels that I would like to be able to watch, but I rather use the Mythtv on my living room T.V.
how can I sync them?

and another question,
does Mythtv has any torrent's plugin or should I use Deluge?
Thank you.

---

### Post by tgm4883 on 2008-10-11
> **orduek said:**
> I checked and chekcked, does anyone uses Mythtv and Miro?
I wonder how to make it work.
Miro has some nice Podcast channels that I would like to be able to watch, but I rather use the Mythtv on my living room T.V.
how can I sync them?

and another question,
does Mythtv has any torrent's plugin or should I use Deluge?
Thank you.

If they are just video podcasts then you can use mythnettv.  I'm not familiar with Miro, but after a quick look on their website I can confirm tht mythnettv works with revision 3 and TED

---

### Post by orduek on 2008-10-12
thanks.
One of Miro's big advatage is the convenient GUI. Which is better than a script.

---

### Post by tgm4883 on 2008-10-12
> **orduek said:**
> thanks.
One of Miro's big advatage is the convenient GUI. Which is better than a script.

What is MythTV except one giant GUI?

---

### Post by agamotto on 2008-10-12
> **orduek said:**
> I checked and chekcked, does anyone uses Mythtv and Miro?
I wonder how to make it work.
Miro has some nice Podcast channels that I would like to be able to watch, but I rather use the Mythtv on my living room T.V.
how can I sync them?

and another question,
does Mythtv has any torrent's plugin or should I use Deluge?
Thank you.

I have been using Miro on my Mythbox for two years now.  I just did the sudo apt-get install bit, and it was placed in the Multimedia menu.  Works well, you just need to drop out of the frontend to use.

---

### Post by orduek on 2008-10-14
so you running Miro in the background all the time?
And if so, do you use another Bittorent clilent (such as Deluge) or You use Miro for that to?

---

### Post by tgm4883 on 2008-10-14
Please explain to me exactly what Miro does?

---

### Post by orduek on 2008-10-14
Miro is a kind of media player but:
It allows you to subscribe to many channels (free ofcourse) of all kind of content.
and, it has a built in bittorent client with RSS reader so you can add subscription to channels that are a rss feed of your favorite series (Prison Break etc.)
Thats it.
It does that with nice GUI but not enough to be media center.
excuse my bad English but I hope it covers the point.

---

### Post by Archmage on 2008-10-15
To answer the question of the topic starter:

Set up Miro to download in a subfoder of your videos in MythTV.

Activate automatical scanning, showing and subfolder search in MythTV.

You either need to active to show unknown filetypes or activate each filetype manual.

Now you can watch the videos in MythTV.

The downsizes are the strange filenames and no preview-picture.

---

### Post by orduek on 2008-10-15
first - thank you.
second, I especially wanted to know if there's a way to get over the srange filenames etc.

and another thing, how do I set Mythtv to automatically scan folder etc.?

thanx.

---

### Post by tgm4883 on 2008-10-15
So I guess that the advantage that Miro has over MythNetTV is that Miro you can search for content?  

But the advantage that MythNetTV has is that it integrates the shows better with MythTV.  


Would that be a correct analysis?

---

### Post by orduek on 2008-10-16
I think that is correct.

---

### Post by Archmage on 2008-10-16
> **orduek said:**
> second, I especially wanted to know if there's a way to get over the srange filenames etc.


Unfortunatly none that I know off. You could go into the video-manager and set there each name that will displayed and what picture you are using. But you would have to do this for each file manual, therefore I think that would be too much work.


> and another thing, how do I set Mythtv to automatically scan folder etc.?

I'm not on my Myth-PC, but I think in the settings of the videos should be an option like automatical scan subfolder.

---

### Post by jbman on 2008-10-16
knoppmyth uses miro as part of its distribution. maybe you can take a look how its used.

---

### Post by agamotto on 2008-10-16
> **orduek said:**
> so you running Miro in the background all the time?
And if so, do you use another Bittorent clilent (such as Deluge) or You use Miro for that to?

No, I run Miro two or three days out of the week in the background when I am not recording much telly, then watch the vodcasts when it suits me.

---

### Post by tgm4883 on 2008-10-16
> **agamotto said:**
> No, I run Miro two or three days out of the week in the background when I am not recording much telly, then watch the vodcasts when it suits me.

Thats the part I don't understand.  Do you subscribe to certain shows for it to download or are you searching for new content and then downloading it?  

Maybe I just don't understand how much new content you look for daily.  I subscribe to a few different shows (TED, scam school, systm to name a few) and MythNetTV checks for new shows daily (or hourly) and downloads them and sticks them in my recording list ready to be watched.  All this happens in the back ground on my backend system.

---

### Post by Archmage on 2008-10-17
It seems that in this case MythNetTV seesm to be much better than miro, since both seems to do basical the same, but MythNetTV seems to be better integrated.

---

### Post by orduek on 2008-10-17
I think you'll just have to check it to see the difference.
maybe there is none. 
I just think Miro has more channels to subscribe to than TED, including HD etc.

---

### Post by tgm4883 on 2008-10-17
> **Archmage said:**
> It seems that in this case MythNetTV seesm to be much better than miro, since both seems to do basical the same, but MythNetTV seems to be better integrated.

That may be the case.

> **orduek said:**
> I think you'll just have to check it to see the difference.
maybe there is none. 
I just think Miro has more channels to subscribe to than TED, including HD etc.

MythNetTV doesn't have channels to subscribe to.  You can subscribe to any Video RSS feed on the internet.  I'm assuming that Miro can do that too.

---

### Post by orduek on 2008-10-19
I will look into Mythnettv - that looks interesting.
it can subscribe to torrent RSS also, right?
Do you have some How-To to this nice plugin?

---

### Post by orduek on 2008-10-21
anyone?

---

### Post by agamotto on 2008-10-21
> **tgm4883 said:**
> Thats the part I don't understand.  Do you subscribe to certain shows for it to download or are you searching for new content and then downloading it?  

Maybe I just don't understand how much new content you look for daily.  I subscribe to a few different shows (TED, scam school, systm to name a few) and MythNetTV checks for new shows daily (or hourly) and downloads them and sticks them in my recording list ready to be watched.  All this happens in the back ground on my backend system.

I watch about 13 regular weekly vodcasts that are subscriptions.  I use the guide built-in to Miro for new shows, click on whatever I might be interested in and cancel when I get tired of one.

I manually start Miro at some point (usually twice) during the week, at night, and let it fetch whatever is 'new,' then watch it when I have the time.

Hope this clears things up a bit.

---

### Post by orduek on 2008-10-27
I really want to try Mythtvnet but find it a bit hard. does anyone have some HowTo or something like that?

---

### Post by tgm4883 on 2008-10-27
> **orduek said:**
> I really want to try Mythtvnet but find it a bit hard. does anyone have some HowTo or something like that?

Did you enable the mythbuntu-testing ppa and install mythnettv-gui?  There are screenshots of the program here  [http://www.mythbuntu.org/image/tid/11](http://www.mythbuntu.org/image/tid/11)

I don't know of any guides, what is difficult about this program?

---

### Post by orduek on 2008-10-29
> **tgm4883 said:**
> Did you enable the mythbuntu-testing ppa and install mythnettv-gui?  There are screenshots of the program here  [http://www.mythbuntu.org/image/tid/11](http://www.mythbuntu.org/image/tid/11)

I don't know of any guides, what is difficult about this program?

I did. and I installed the mythnettv-gui also.
when starting it he asks me to create some config file...
and I can't subscribe to anything (probably I have to create the file first).

thanks.

---

### Post by tgm4883 on 2008-10-29
> **orduek said:**
> I did. and I installed the mythnettv-gui also.
when starting it he asks me to create some config file...
and I can't subscribe to anything (probably I have to create the file first).

thanks.

You should be able to go to File > Set Datadir and set it.  A good place for it to be set to is /var/lib/mythtv/mythnettv/

---

