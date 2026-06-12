---
title: "How to setup a pppoe conection"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by andrei C on 2009-07-04
Hi everyone!
I just tried the Xubuntu 9.04 Live CD and it seemed pretty nice.I was able to view all my widows partitions and the system monitor said that only 160 MB of RAM were used.As you probablly figured out, I'm using it for an old computer, 1600MHz Athlon XP and 256 MB of RAM.Windows just doesn't run nice on this configuration.
But there was one problem: the internet connection.I have 2 network cards in my computer, but I use only one.Xubuntu saw something, if i right click on the network icon and choose setup or something like that, it sees two conections.But I can't setup either of them.I just need a PPPoE conection.In windows you do that by making a manual connection, so I tryed that, but instead of asking my the provider name, it just wants some numeric adresses.
So how do I do it? Since the computer is very old, I only use it for internet.If internet doesn't work then the computer is useless.

P.S: I haven't installed anything yet.It would be of great help to try setting up an internet connection in the Live CD, just to make sure it works.And I do not have a router.

---

### Post by superprash2003 on 2009-07-04
go to system->preferences->network connections  . and under DSL tab , click on ADD and then fill in details.. before this , you should make sure you are able to access your modem

---

### Post by andrei C on 2009-07-04
Thanks! I'll try that.

---

### Post by andrei C on 2009-07-04
[LEFT]Thank you [superprash2003]("http://ubuntuforums.org/member.php?u=229099")! You really helped me.It worked!I was able to setup the internet conection in the Live CD mode, whithout actually installing Xubuntu and I was able to browse the inernet!And this of an Live CD!Now I know for sure setting up an PPPoE conection is easy, so I'll definately give Xubuntu a chance by installing it.

Just one thing: I couldn't find the Preferences menu anywhere.Not in Settings and not in System.So System>Preferences>Network Connections didn't work.Instead, to get to the DSL tab, I just right clicked on the connection icon from the panel bar and then chose Settings or Preferences or something.And a window apeared which had the DSL tab.From there on, I just did like you said, I pressed the Add button and I entered the username and password and ISP name.
One question: I entered the ISP name in the Connection Name field, is that any good??In the Service Name field I didn't enter anything :).I just put the username and the password, that's it.Does the ISP name go in the Service Name field???It worked like I did it, but maybe it wasn't the best way to do it. :)

Anyway, thanks a lot.I was impressed.
[/LEFT]

---

### Post by superprash2003 on 2009-07-04
ah, i guess the menu options are different xubuntu , havent used that since a while..the service name field can be anything , you can enter whatever you wish!!doesnt matter..

---

### Post by andrei C on 2009-07-04
Thank you [superprash2003]("http://ubuntuforums.org/member.php?u=229099")! You are really kind, answering all my silly questions.I really appreciate your help.

---

### Post by petrumadalin on 2010-01-19
Hi everyone,
 
I am new on Linux and I am using Xubuntu on PIII. The OS is wonderfull!! 
The only problem I have is that I am trying to setup the Internet connection PPPOE and no succes. I tryed every options, included the one above, but it doesn't work. I have a cable Internet Provider and I know from the win xp(the other OS from the same PC, which I want to get rid of) that this is  PPPOE connection. In winxp I only need a name and password and user. Can anyone help me?
 
Cheers
Madalin

---

### Post by ajsc on 2010-02-15
Hope this works for you.  In the network manager right click the icon and disable network connections i.e clear the check mark.  Then go to edit network connections.  Click on the dsl tab.  Select any connection name for example dsl1, dsl2 etc and delete all one by one.  The close the window.  Again right click the n.m. icon and go to edit option and the select the dsl tab. Make an new dsl1 connection but do not enable for all users.  Now close the window and try connecting the dsl1 connection.

---

