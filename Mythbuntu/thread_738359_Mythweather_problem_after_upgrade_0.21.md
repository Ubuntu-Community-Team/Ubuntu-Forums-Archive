---
title: "Mythweather problem after upgrade 0.21"
date: 2008-03-28
forum: Mythbuntu
---

### Post by axelsvag on 2008-03-28
I live in Europe and I have enjoyed the mythweather feature that work decently in Europe in 0.20. After upgrade to 0.21 I just can get two menus, current weather (but it gives garbage info in the active screen) and three day forecast with good results. If I look in the [HTML]http://www.mythtv.org/wiki/index.php/MythWeather[/HTML] There seems to be at least 7 menus reachable. If I look  on the site above there seems to be just right that only two menus are reachable for Europe but if I use the [HTML]http://www.weather.com/maps/ 
[/HTML] I can reach cities in Europe. 
My question is:
Is it possible to get weatherinfo for Europe by modifying the scripts for mythweather? Is it possible get back the good service from 0.20 version?

---

### Post by foxbuntu on 2008-04-02
I would suggest filling a bug. MythWeather doesn't use 'scripts' persay, but it is coded into the backend portion of MythWeather, you are always welcome to attempt to edit the source and later supply a patch though.

---

### Post by volkswagner on 2008-04-02
I have not seen any descriptive response to the change in .21 concerning mythweather.  I have only found one other thread on this topic.

[http://ubuntuforums.org/showthread.php?t=727064&highlight=weather+mythweather]("http://ubuntuforums.org/showthread.php?t=727064&highlight=weather+mythweather")

With my poor reasoning this leads me to believe one or all of the following to be true.

[LIST=1]
[*]I am part of a small group that upgraded to .21 and use mythweather.
[*]The majority of the upraders using mythweather are happy with the new sources.
[*]I am doing something wrong to get the weather as it was.
[/LIST]

I am wondering why the sources have changed.  I thought it was so cool to have my hometown displayed on the weather screen vs. my nearest large city.

Can anyone explain WHY the change.  Often when knowing why, it eases the mind.

---

### Post by foxbuntu on 2008-04-02
Not sure the reason for the change. But I might suggest heading over to #mythtv-users and asking questions, many of the devolpers hang out in there to answer these kind of questions.

---

### Post by volkswagner on 2008-04-02
Great suggestion foxbuntu.  It is always nice to know why.

From 
[http://www.mythtvtalk.com/forum/viewtopic.php?t=7224&highlight=mythweather]("http://www.mythtvtalk.com/forum/viewtopic.php?t=7224&highlight=mythweather")   [http://www.mythtvtalk.com/forum/viewtopic.php?t=5613&highlight=mythweather]("http://www.mythtvtalk.com/forum/viewtopic.php?t=5613&highlight=mythweather")

> 
Mythweather has been broken in the released version of mythtv for quite some time now. The website it scrapes changed the format of the page which is what did it. Ordinarily it would just have been fixed to make it work with the new page layout but scraping the site is against its usage terms & conditions.

With that in mind, a Google summer of code project to revamp mythweather was resurrected and merged into trunk. It works but is a bitch and a half to configure. No, it won't be backported into -fixes but yes it will be part of the 0.21 release.

Thought this was funny:
> 
Mythweather is broken because the site it scrapes to get its data has changed.

A fix is in the works but the jury is still out on when it'll be ready for prime-time.

Until then, look out of your window 

That was easy.

---

### Post by axelsvag on 2008-04-05
Ok I´ll try to understand the info you are giving me.
Very few people seems to use the mythweather so the interest to get i to work is small. That seems to be a reasonable answer.

The other thing is related to something that has happened to mythtweather when the upgrade to 0.21 occurred. If my memory is correct the mythweather got broken in 0.20 then the 0.20.2 came and mythweather went back working OK again. And now the mythweather is a pain in the *** again. My question is now how can we european get the 0.20.2 version of mythweather back? At least it worked reasonable good. Or we could get some advice how to use other db sources more common in Europe. There seems to be some scripts in the mythtweather folder that does not look impossible to rewrite or am I making things to easy now? In mythnews it is very easy to change db so you can get whatever newspaper you want.

What I say is, the info about the trunk broken seems to be related to the 0.21 and not the 0.20.2 or did I got it completely wrong?

Ok I can see when I read my text that it looks naive but I really liked mythweather and wish it all good for the future.

---

### Post by laga on 2008-04-05
In 0.20 and before, Mythweather used one data provider. Everything was hardcoded. Then something broke and the developers found out that they couldn't use that data source because it as against their terms of use.

The new Mythweather is much more flexible. It uses scripts to query data providers and then displays the output of those scripts. If you want better data, you need to write a new script (or pay someone to do it, or just look out of the window ;)).

*edit:* For MythTV 0.20.x in Ubuntu, Mythweather was patched to make the old data source work again. That's not possible anymore in 0.21.

---

### Post by axelsvag on 2008-04-05
Ok, I understand. I´ll better start to learn more to be able to contribute more to the mythbuntu society.

---

