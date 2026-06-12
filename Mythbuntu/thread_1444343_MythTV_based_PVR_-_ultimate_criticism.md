---
title: "MythTV based PVR - ultimate criticism?"
date: 2010-04-01
forum: Mythbuntu
---

### Post by oz238 on 2010-04-01
Here is my mini blog about MythTV based personal video recorder:
[http://wyspajacka.info/index.php?option=com_content&view=category&layout=blog&id=45&Itemid=111](http://wyspajacka.info/index.php?option=com_content&view=category&layout=blog&id=45&Itemid=111)

I would to write it as a topic on forum but when I finished I realised that it took a lot of text. So I added it to my personal www site.

What I expect with creating topic like this? We know what is MythTV and what it can do for you. But there are many aspects which are not good. So please, write them, if you want.

Don't post answers like: "I don't like your opinion because it is wrong", "MythTV is the best so your opinion is wrong", "MythTV is 0.2x, so it is still beta". Be constructive in your answers, please. I spend some time to write this miniblog. I didn't write: "I don't like MythTV because it is bad". I wrote every aspect which disappoints me and I belive it could be better. Write the answers in this topic in the same manner. Tell me: if you agreed, why? If you disagree, why? Write the reasons. What is missing in my blog?

Last note: I wrote this about the whole system, not only about MythTV or Mythbuntu.

---

### Post by williammanda on 2010-04-01
I read your blog and from what I can tell alot of your problems stem from the under rated hardware that you are using. I currently have four computers ranging from a core 2 quad to pentium 4. The P4 computers are only used as frontends and nothing else but the others are used for mythtv  as well a regular desktop computer. Another issue is you need to understand that linux isn't bleeding edge computing. If you want that then stick with windows. With that in mind, stick with the hardware that works or start programming your own drivers.

---

### Post by sfuse on 2010-04-02
Hard for me to take your criticisms seriously with all the grammatical errors in your text.  
 
I tried windows MCE briefly but quickly found too many annoyances.  For me, being a bit of a hacker by nature, MCE offers little if any opportunity to correct or change any of those annoyances.  For the average joe I would say an STB with a built in DVR is the better solution.  Only true geeks want to mess with using a computer as a PVR.  So in that sense I think MythTV should be the more appealing option.

---

### Post by iamlindoro on 2010-04-02
Most of your complaints are based on apparent misunderstandings on your part more than they are about Myth's shortcomings.  The two that stand out are your conclusion that myth doesn't need a database (and that everything should be in text files), and the alleged "requirement" to know SQL to edit channels.

To your first point, Myth *must* have a database for a number of reasons.  First off, Myth's scheduling and program information must live in a database to get anywhere near the performance necessary to work, and of the available open source databases, only MySQL performs fast enough to accommodate the scheduler queries, which are extremely large, CPU intensive affairs.  If the scheduling was done in custom code, parsing text files, especially with tens of thousands of programs worth of information to parse though, it would run dozens, if not hundreds of times slower.  Myth uses a database because it is the only way to parse the vast amounts of information necessary with acceptable speed.  It's also convenient that one can lose a frontend entirely, connect a new one with the same hostname, and be functional with the exact same setup.  You argue that text files are "open" and that anyone could write an editor, but MySQL is equally "open" and one can interface with it with a settings editor just as easily-- however, we prefer that nobody directly edit their database as much of the database information is delicately interwoven in a way that is necessary and liable to break if someone edits it without knowing what they are doing.

Regarding the channel editor, you can absolutely mass-edit channels in the channel editor in mythweb.  No SQL knowledge required, and all presented in a single web form.

The other stuff I won't delve in to, but it doesn't help that you are hacking in softcam clients and DVB loopback adapters, meaning you are already complicating things beyond the point of "install and go" being a realistic goal.  There was not a single issue in your critique that I could not definitively say was a configuration error on your part.

Could Myth be easier to configure to prevent you from making these mistakes?  Absolutely, and that's a near-term goal.  But is it Myth's fault when something gets misconfigured, or the user doesn't understand why things are the way they are?  Absolutely not.

---

