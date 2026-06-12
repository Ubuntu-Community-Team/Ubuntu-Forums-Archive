---
title: "Unable to use any Google Talk &quot;compatible&quot; tool for Voice"
date: 2008-05-24
forum: Multimedia Software
---

### Post by jvpgomes on 2008-05-24
Hi!

Does any one have been able to communicate, using voice, with any Google Talk host, in Linux?
Any one has a good solution?

First, I tried Jabbin. I successfully installed it and I can use it for chat. However, when I try to make a VoIP call, I cannot hear the other person and the other person cannot hear me. I just hear noise. 
I thought that it was some kind of problem with the sound system, but apparently, everything is ok. I tried with Alsa and with OSS, and I also tried running Jabbin using aoss.

After that, I tried Tapioca/Telepathy. I installed everything. Apparently, it is all ok.
Then I needed a client. I installed Landell. However I keep receiving two different error messages when I try to connect to Google Talk.
The first connection attempt returns the message:

[I]Argument cannot be null.
Parameter name: value[/I]

After that, I receive the message:

*org.freedesktop.Telepathy.Error.TpError_NotAvailable: Error acquiring bus name org.freedesktop.Telepathy.Connection.gabble.jabber._*<my user name>*_gmail_com_Landell: Connection manager already has a connection to this account.*

I used telepathy-inspector to understand what is happening. But, apparently the connection was well established.

So, I tried another client: Ereséva. After a long journey, I have successfully installed it. But, its performance is depressing... I could write text, but I couldn't see what I was writing and I couldn't receive any text. Also, I wasn't able to make a VoIP call.

As a last and desperate attempt, I tried to use Google Talk over Wine. However, I could connect to the server...

Does any one knows a good alternative to make Google Talk VoIP call through Linux? I do I have to install Windows?

Thank you for your help!

---

### Post by Abhinavhardikar on 2009-02-08
You could use empathy for voice calls over google and use mic boost for better performance.

In synaptic search for empathy(alternative for google talk) and gnome-alsamixer(for mic boost).

I personally use empathy and is very good

for more info you may go to [http://live.gnome.org/Empathy]("http://live.gnome.org/Empathy")

Hope it's not too late

Abhinav;)

---

### Post by jvpgomes on 2009-02-08
Hi!

Thank you a lot! It really works.

However I can't hear any call ringing... which turns difficult to notice that somebody is calling me.

Did you manage to have call alerts working?

Thank you!

---

