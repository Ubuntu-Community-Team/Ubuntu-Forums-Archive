---
title: "Official Microsoft Codecs (and Flash Player)"
date: 2008-10-29
forum: Multimedia Software
---

### Post by Andre_Macd on 2008-10-29
Hi I'm having trouble streaming Windows Media from inside a web browser (Firefox). If I was to buy the codec pack from the Ubuntu store ([http://shop.canonical.com/product_info.php?products_id=242&osCsid=b37d59321216c966d3b29ddbb1ad9738]("http://shop.canonical.com/product_info.php?products_id=242&osCsid=b37d59321216c966d3b29ddbb1ad9738"))would that include an in browser player plug-in that would play all Windows Media without any extra playing around?

Also I've looked around and it seems to be quite a common problem but Flash on Ubuntu really does use a ridiculous amount of resources, how is something like that even possible? A simple Flash menu like on [http://nz.yahoo.com]("http://nz.yahoo.com") stresses my computer more than playing multiple high def videos simultaneously or a complex 3D game?

Cheers for any responses all in all I've been really pleased with Ubuntu and hope to be sticking around the forum for some time :)

---

### Post by Bakon Jarser on 2008-10-29
You should upgrade to flash 10.  It is much better.  As for your video problems this thread should help.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by ad_267 on 2008-10-29
What is the website you're having problems with? You shouldn't need to purchase the codec pack, I think that's more aimed at people that want to make sure they have legally purchased codecs, rather than ones from the ubuntu-restricted-extras package.

That xtra!yahoo site seems to use way more cpu than it should. Most flash sites work fine for me but that one just seems really bad. You can use the flash block plugin for firefox to block flash unless you click on it.

---

### Post by Andre_Macd on 2008-10-29
I've upgraded to Flash 10 and it does seem to help flv videos considerably but a modest swf menu like nz.yahoo.com is still treated like a mamoth task. If someone could go to [http://nz.yahoo.com]("http://nz.yahoo.com") have a look at there system monitor , drag the scroll bar up and down and minimize and maximise the window and tell me the results please?

---

### Post by ad_267 on 2008-10-29
Yeah nz.yahoo makes my computer go crazy too, xorgs cpu usage skyrockets. Like I said, you can use flash block, but that's not really a great fix.

---

### Post by Andre_Macd on 2008-10-29
> **ad_267 said:**
> What is the website you're having problems with? You shouldn't need to purchase the codec pack, I think that's more aimed at people that want to make sure they have legally purchased codecs, rather than ones from the ubuntu-restricted-extras package.

That xtra!yahoo site seems to use way more cpu than it should. Most flash sites work fine for me but that one just seems really bad. You can use the flash block plugin for firefox to block flash unless you click on it.

Cool cheers for doing that. 

And cheers Bakon Jarser I'l go through the steps provided in the thread and post back after that, also I guess what I was asking is does the [Windows codec pack]("http://shop.canonical.com/product_info.php?products_id=242&osCsid=b37d59321216c966d3b29ddbb1ad9738") I mentioned (or any free or non free software) have an official Windows Media plugin for an Ubuntu web browser?

---

### Post by Bakon Jarser on 2008-10-29
You are confusing codecs and media players, a common mistake.  A codec allows you to decode certain media types.  Once you have the codec a media player uses it to decode the media format.  The link you provided will get you a codec for decoding windows media formats.  Firefox may play inside firefox with certain plugins or it may launch an external player depending on how you have it set up.

Now, the link I provided will take you through downloading these codecs for free and setting up a plugin to play them in firefox.  There are legal reasons that these are not installed by default on Ubuntu.  I personally don't think it is illegal to download and use these codecs, but I am not a lawyer and this is not legal advice.  Here is a link to [more info. ]("http://www.madpenguin.org/cms/?m=show&id=8093")

---

### Post by gandaran on 2008-10-29
> what I was asking is does the Windows codec pack I mentioned (or any free or non free software) have an official Windows Media plugin for an Ubuntu web browser?

no, you still have to use the totem-mozilla plugin for online video streaming
the fluendo codecs have better support for every wmv format, better video color and dvd menu display in totem, the free gstreamer plugins don't play some wmv format.

---

