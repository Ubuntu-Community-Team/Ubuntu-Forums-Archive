---
title: "KNetworkManager does not auto-start connection after Resume"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Firestem4 on 2009-03-04
Whenever I put my laptop into standby and I resume (8.10)KNetworkManager does not automatically resume its last internet connection (Similar to its auto-connect feature). Is this a bug/by design? Is there some workaround I can do to fix this?

Any help would be greatly appreciated. Thanks in advance!

---

### Post by yther on 2009-03-04
I got the same difficulty here... for the moment I'm working around it by simply not using suspend, or doing "sudo service NetworkManager restart" when I need to.  I should find out if there's a way to trigger scripts when resuming.  [searches]  Hm, there may be, but it's nothing I can solve in 5 minutes, so leaving it for later.  :(

There's at least one [bug about this behavior]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264683"), as well.  You may find some useful info, or links to it, in there.

---

### Post by Firestem4 on 2009-03-04
I was considering potentially creating a script..(or well copying it from someone who has...since i know very little BASH   Me<----am fairly new to linux).

I wouldn't know where to begin when it comes to executing a script on resume...Ive only made one script so far which kills my Firefox process and starts Firefox (works flawlessly hehe. Firefox when exited didn't dump the process, so I couldn't open it up againn till I did)

If you have any luck with this in the future, Could you please notify me?

---

### Post by Firestem4 on 2009-03-04
HAH! Would you look at that...

I just installed todays updates and one of those included a Knetworkmanager update. Guess what it fixed?

Ironic lol.

---

### Post by lyjn0303 on 2009-03-04
One day, a Zen master in order to inspire his disciples, to his disciples a stone, called him to the vegetable market, and try to sell it, this rock great, very beautiful. But the master said: "Do not sell it, just try to sell [**PRADA SHOES**](http://usa-ad.nikeshoeshall.com/PRADASHOES.html). To observe the more some people ask, and then told me that as long as it can sell in the market, the number of vegetables." This person went. In the vegetable market, many people want to watch a rock: it can be a very good small ornaments, our children can play, or we may take it as that used in dishes steelyard weight scales. So they were a price, but only a few small coins. That person back. He said: "[**COACH BAGS**](http://usa-ad.nikeshoeshall.com/COACHBAGS.html) can only sell a few coins."      Master said: "Now you go to the gold market and ask people there. But do not sell it, light to ask the price." Returned from the gold market, the disciples very pleased, said: "These people are great. [**AIR MAX**](http://usa-ad.nikeshoeshall.com/) are willing to work out to the 1000 money. "      Master said: "Now you go to jeweler there, but do not sell [**NIKE SHOES**](http://usa-ad.nikeshoeshall.com/)." Where he went to the jeweler. He could not believe that they actually willing to 50,000 out of money, he did not want to sell, and they continue to raise prices - they are out to 100,000. However, this person said: "I do not intend to sell it." They said: "We are out of 200,000, 300,000, or the number of how many you want, as long as you sell!" [**AIR JORDANS**](http://usa-ad.nikeshoeshall.com/) person said: "I can not sell, I just ask ask price. "He could not believe that:" These people are crazy! "He felt the market price of vegetables has been sufficient.      He returned back to the stone master said: "We do not intend to sell it, but now you understand, this depends on you, do you have a touchstone, understanding. If you are living in the vegetable market, then you have only that understanding the market, you will never understand the higher value. "

---

