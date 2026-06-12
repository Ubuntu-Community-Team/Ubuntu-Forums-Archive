---
title: "Snapstream Firefly almost working"
date: 2009-02-18
forum: Mythbuntu
---

### Post by thephantomlord on 2009-02-18
Hi All,

I am a recent convert to Mythbuntu and so far I love it.  It recognized my Hauppuage Wintv card and Motorola cable box with very little intervention, yay.

Now I'm trying to get my Firefly remote working and I've got it very close with help from this thread: [http://ubuntuforums.org/showthread.php?t=884972&highlight=firefly](http://ubuntuforums.org/showthread.php?t=884972&highlight=firefly)

And this instruction:

[I]even though it worked before rebooting. Lastly, running 'lircd' returned to a prompt without anything at all to say. After looking for a long time on google and doing much research, I found that by adding '-d /dev/lirc/0' to lircd to make

lircd -d /dev/lirc/0[/I]

From here: [http://www.mythtv.org/wiki/Talk:Lirc_on_Ubuntu_Dapper](http://www.mythtv.org/wiki/Talk:Lirc_on_Ubuntu_Dapper)

I did have to change the command to **lircd -d /dev/lirc1**

And now I am getting working buttons in MythTV and results from irw.

My question is a simple one I hope.  How can I force lirc to load automatically with the extra parameters I've specified above?



thanks in advance and thanks to the folks on those two previous threads too.

---

### Post by thephantomlord on 2009-02-19
Anyone?  This seems like it should be a pretty simple thing to do, I just need to change the commands lirc uses when starting up automatically.

thanks

---

