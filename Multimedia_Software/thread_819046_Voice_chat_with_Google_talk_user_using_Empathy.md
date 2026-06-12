---
title: "Voice chat with Google talk user using Empathy"
date: 2008-06-05
forum: Multimedia Software
---

### Post by vigyani on 2008-06-05
Hi

Want to voice chat with Google Talk user!!
On Ubuntu 8.04 Empathy can be used to voice chat with Googletalk users.

On an updated Ubuntu 8.04; Using Synaptic Package Manager add the following third party repository and install the packages given below.

Instructions:
System --> Administration --> Synaptic Package Manager

Go to Settings->Repositories
Go to Third Party Software --> Add;
Enter the following line in APT line:

 ```
 deb http://ppa.launchpad.net/telepathy/ubuntu hardy main 
```

Close and Reload

Search and mark the following packages for install:
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

and Apply i.e. install.

Use the latest packages as older packages do not allow Gtalk/Jingle VOIP.

After installing start Empathy (Applications --> Internet --> Empathy Instant Messenger)

Configure your gmail account.

Cheers

References:

[LIST=1]
[*][https://launchpad.net/~telepathy/+archive]("https://launchpad.net/%7Etelepathy/+archive")
[*][http://ubuntuforums.org/showpost.php?p=4852798&postcount=21](http://ubuntuforums.org/showpost.php?p=4852798&postcount=21)
[/LIST]

---

### Post by ramkumail on 2008-06-05
hi vigyani, I cant wait to try this. I am not at my linux box now. does it have proxy support? my university allows access only through a proxy.

---

### Post by vigyani on 2008-06-05
Hi
I am running it behind a transparent proxy (it does not require authentication). 

There are no options to configure proxy. Not sure if it would accept System wide proxy settings.

Cheers

---

### Post by ramkumail on 2008-06-05
mine requires authentication. I tried and didn't manage to connect. hope that they include proxy support very soon.

---

### Post by jasidog on 2008-06-06
Hi vigyani!

Thank you very much for the guide, I'm yet to try things out (All my contacts are suspiciously offline :D ) but it seems to have installed perfectly.

Assuming it all works well, this will be so useful for me. I have one  person in particular that I always use gtalk with and when we want to use voice I need two applications open before now. 

Thanks!

---

### Post by MmmmJoel on 2008-06-08
Does anybody know how to configure which sound devices Empathy should use?

My default PulseAudio device output is not the same device output I would like Empathy to use.

Currently, the only way I know to work around the problem is to select a new default output device each time I want to use Empathy to chat using padevchooser.

With the new IM/VOIP stack, I'm not sure if this would be an Empathy option or Telepathy option.

Thanks,
Joel - [www.onlyjoel.com]("http://www.onlyjoel.com")

---

### Post by Homey on 2008-06-11
> **vigyani said:**
> Hi

Want to voice chat with Google Talk user!!
On Ubuntu 8.04 Empathy can be used to voice chat with Googletalk users.

On an updated Ubuntu 8.04; Using Synaptic Package Manager add the following third party repository and install the packages given below.

Instructions:
System --> Administration --> Synaptic Package Manager

Go to Settings->Repositories
Go to Third Party Software --> Add;
Enter the following line in APT line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

Close and Reload

Search and select the following packages:
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

Use the latest packages as older packages do not allow Gtalk/Jingle VOIP.

Cheers

References:

[LIST=1]
[*][https://launchpad.net/~telepathy/+archive]("https://launchpad.net/~telepathy/+archive")
[*][http://ubuntuforums.org/showpost.php?p=4852798&postcount=21]("http://ubuntuforums.org/showpost.php?p=4852798&postcount=21")
[/LIST]

vigyani, Thank u so much for this simple step by step tutorial
I manage to install all the packages u mention .. in now time I added my googletalk account to empathy and .. bingo :) 
I got all my contact list and start to talk Voice (PC 2 PC) 
the sound is perfect for both playback & mic (on my side), only the receiving end can listen to there echo !!

_TWO notes:_
1 - when some 1 call me there is NO ring tone except u see the icon of the emapthy is flashing ! (u have to click on it and hit the start call button) 

2 - There is NO email notification also

but anyway .. Voice Calls WORKS 100%
guys, keep the excellent job  

my best regards

---

### Post by mohitsrms on 2008-06-21
Thanks a Ton Vigyani .... finally i got something working for me .... well one quest..  i was not able to have a voice chat with my frnd who was on VISTA ... is thr ne compatibility issue ...

---

### Post by justynbutler on 2008-06-21
Yep, had to open pavucontrol and unmute my mic stream but I could then talk to another Ubuntu user who had also installed the packages.

At last, some real progress! Definitely in need of some configuration options though.

---

### Post by sergiom99 on 2008-06-26
hey.
I installed all mentioned packages w/o errors and when I try to run it:
```
sergio@kubuntu:~$ empathy

(empathy:17426): tp-glib-WARNING **: Failed to connect to starter bus: Failed to execute dbus-launch to autolaunch D-Bus session
```

---

### Post by sergiom99 on 2008-06-26
Think I fixed it with
```
sudo apt-get install dbus-x11
```
hope this doesnt 'break' anything else.

---

### Post by sergiom99 on 2008-06-28
I cannot talk! I make a call and get a screen like this: 
 [[IMG]http://img246.imagevenue.com/loc148/th_78968_instant4nea1_122_148lo.jpg[/IMG]](http://img246.imagevenue.com/img.php?image=78968_instant4nea1_122_148lo.jpg)
Its all grayed-out and I cannot answer a call either.
I got the mic icon flashing in the panel and when I click it, I got this same window.
Any other thing I should set up? There is no sound/video preferences in Empathy.

---

### Post by itisbasi on 2008-06-28
Yep, I've got the same problem as sergiom99......

---

### Post by lupa18 on 2008-07-04
I have no problem on instalation.. but when I tried to login.. I get an "Authentication error"

thanks

---

### Post by guhanr on 2008-07-07
@Vignani: Your instructions worked great. Thanks. 

However, after installation, I cant get it to connect. I get this error (scrshot attached). 
> GTalk0 
Authentication error. 

Any other settings that need to be changed, to get this going? Maybe some of the others who have been successful with empathy can share experiences with any setting changes they have made to get this to work?

Advice, anyone?

-Guhan

---

### Post by guhanr on 2008-07-07
UPDATE : I used my [email]username@gmail.com[/email] and it seemed to login alright [basically added @gmail.com to the userID field and it worked. Woohoo! 

Now, my sound card and me are having all sorts of problems! :)

---

### Post by guhanr on 2008-07-07
UPDATE : I used my [email]username@gmail.com[/email] and it seemed to login alright [basically added "@gmail.com" (no quotes) to the userID field and it worked. Woohoo! 

Now, my sound card and me are having all sorts of problems! :)

---

### Post by mthakur2006 on 2008-07-09
hi
i installed empathy as per your instructions.
how do i actually initiate a call?
also, it didn't ask me to configure my mic or anything??
i have installed all the right versions i think.
any help will be appreciated.
ta

---

### Post by sergiom99 on 2008-07-09
> **mthakur2006 said:**
> 
how do i actually initiate a call?
also, it didn't ask me to configure my mic or anything??

you click on the mic icon besides any of your contact, and then you get a screen (in my case) without any possibity of doin anything, its all grayed out.

---

### Post by defaulk on 2008-07-09
This didn't work for me.  I added the repository and reloaded, but when I select the telepathy-stream-engine, it says this package has unresolvable dependencies.  What do I need to do?  I'm running the 64-bit version of Hardy.

telepathy-stream-engine:
 Depends: libfarsight0.1-3 but it is not going to be installed

---

### Post by mthakur2006 on 2008-07-10
> **sergiom99 said:**
> you click on the mic icon besides any of your contact, and then you get a screen (in my case) without any possibity of doin anything, its all grayed out.

there is no mic icon beside the contact!

---

### Post by n77 on 2008-07-10
Check your version.  If you have 0.22.1 you can't vc.

Empathy version has got to be 0.23.3.

sudo apt-get update
sudo apt-get upgrade

if that does not work, open synaptic package manager and look for upgradable packages and mark them.  Some packages may fail to mark.  Don't worry just mark the ones you can one by one and upgrade.

---

### Post by mthakur2006 on 2008-07-11
it is the latest version, still no mic icon. i am attaching the screenshots.

---

### Post by mthakur2006 on 2008-07-11
bump
i need help with these please
this is the only reason for me having to dual boot windows :(

---

### Post by sergiom99 on 2008-07-11
sorry, I am also clueless.
It doesnt work in my Kubuntu either.

---

### Post by peacewithall on 2008-07-11
Thanks for this works perfectly on my Ubuntu 8.04, sound quality of skype has been unbearable, this has saved me, because most people I know have Windows, and up until now I was left out, as I could only use Skype, and with that terrible noise it produced, hardly recognisable as a voice, did not make me want to use it.

Anyway thank you very much, I do really appreciate this guide a lot :).

---

### Post by mthakur2006 on 2008-07-12
> **mthakur2006 said:**
> it is the latest version, still no mic icon. i am attaching the screenshots.

Never mind y'all -- it WORKS!
just two things:
-sound quality is not as good
-mic starts screaming when placed near the speakers which it didn't do in windows ??

ta

---

### Post by sergiom99 on 2008-07-12
how did you make it???
this is what i get in konsole when launching and the closing empathy.

```
sergio@kubuntu:~$ empathy
** (empathy:22495): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:22495): DEBUG: mission_control_get_presence_message_actual: MC not running.

(empathy:22495): libebook-WARNING **: Can't find installed BookFactories

(empathy:22495): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
** (empathy:22495): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:22495): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:22495): DEBUG: mission_control_get_tpconnection: MC not running.
sergio@kubuntu:~$

```

---

### Post by sergiom99 on 2008-07-12
am I missing some packages? Is there a bug that needs to be filed somewhere?

---

### Post by vigyani on 2008-07-13
Sorry for not checking this post for long time.

Empathy works for me and I use vioce chat. Vioce quality is good. May you have to configure mic and speaker to get better quality.

If I run it from terminal i.e. CLI; I do get some debug information but empathy works without any problems.

Once you start emapthy, you need to configure your account information.
Go to edit and configure your account.

The debug information I get is given below; but this does not stop me from using empathy;
laptop-01:~$ empathy
** (empathy:10081): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:10081): DEBUG: mission_control_get_presence_message_actual: MC not running.

(empathy:10081): Gtk-WARNING **: Global Menu Library(libgnomenu) not found. Fall back to GTK code for handling menu bar. GTK-aqd is intended to provide Global Menusupport from legacy GTK applications. 
** (empathy:10081): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:10081): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:10081): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:10081): DEBUG: mission_control_get_tpconnection: MC not running.

Hope this helps.
regards
Vig

---

### Post by jasidog on 2008-07-13
Works fine for me too, just discovered after reading this that if i run it from the terminal I get similar errors - 

```
jasidog@boxer-box-nix:~$ empathy
** (empathy:9074): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:9074): DEBUG: mission_control_get_presence_message_actual: MC not running.
** (empathy:9074): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:9074): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:9074): DEBUG: mission_control_get_tpconnection: MC not running.

```

However I had no idea of those messages before as it seems to work fine. The voice quality is decent, perfectly usable. Not as good as Skype I'm finding though. Which has limited my use of Empathy. 

I'm not sure why that would be as in windows I've never noticed a really obvious difference in quality between the two apps.

---

### Post by sergiom99 on 2008-07-13
Filed a Bug for Empathy:
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)

---

### Post by sergiom99 on 2008-07-14
got it working... sort of.
please look the bug report>
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)

Now gotta solve the crappy sound.

---

### Post by loveunit on 2008-07-23
I've followed these instructions, and have installed empathy, no problem, I get the same errors as listed when opening from terminal, however I cannot make any type of account connect. 

I've never seen one user, and so cannot try calls or chats.

can anyone please offer some help -- I wonder if this is connected to the network manager bug, as I connect my 3G USB via a script, and so NM never thinks I'm connected, this is part of the reason for moving away from pidgin, which I have to reconnect all the time.

thanks in advance

---

### Post by vigyani on 2008-07-23
Hi

Today on Hardy 8.04.1 fresh install and updated, I installed Empathy following the instructions. Empathy works fine and I can voice chat.


Cheers
Vig

---

### Post by vigyani on 2008-07-23
Hi
Are you able to login i.e. does Empathy show your online status as "Available"?
Do you see green icon on the panel?

regards
Vig


> **loveunit said:**
> I've followed these instructions, and have installed empathy, no problem, I get the same errors as listed when opening from terminal, however I cannot make any type of account connect. 

I've never seen one user, and so cannot try calls or chats.

can anyone please offer some help -- I wonder if this is connected to the network manager bug, as I connect my 3G USB via a script, and so NM never thinks I'm connected, this is part of the reason for moving away from pidgin, which I have to reconnect all the time.

thanks in advance

---

### Post by loveunit on 2008-07-26
Hi, sorry for the delay.

I am not able to login, Empathy is always a grey square.

I've tried a number of different accounts and settings, is there a test account I can try to login and see if that work, I remember reading something somewhere about that?

any help is greatly appreciated.

thanks.

---

### Post by vigyani on 2008-07-26
I understand to use google talk  account you have done the following:

1. In Empathy, Edit --> Accounts gtalk0 is checked
2. For Gtalk account you have to give Login ID [email]user-name@gmail.com[/email]
3. Server is: talk.google.com
4. Port is 5223, and 
4. Use old ssl is checked

Actually for advance options default setting work.
I am not aware of a test google talk account.
Do let me if it works.

---

### Post by loveunit on 2008-07-27
Hi Vigyani.

thanks for your reply, I have added the account exactly as suggested, but still it does not login.. once I had a 'correction error' notice, and the gnome foot symbol moved as it tried to connect, but since then nothing.

when I installed using symaptic I also had a few notices about unresolvable dependencies, could this be the issue?

thanks for any advice.

---

### Post by vijay_uforum on 2008-07-29
I am unable to create the account :(
Followed the above steps but no use...
version Empathy 0.23.3

getting the foloowing error in terminal
** (empathy:6256): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:6256): DEBUG: mission_control_get_presence_message_actual: MC not running.
** (empathy:6256): DEBUG: check_for_accounts: No enabled accounts
** (empathy:6256): DEBUG: check_for_accounts: No enabled accounts
** (empathy:6256): DEBUG: check_for_accounts: No enabled accounts

---

### Post by vijay_uforum on 2008-07-29
You have to fill the password too. Incomplete accounts are not saved by MC. That's not an empathy bug, it's a MC feature :)

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/118800](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/118800)

Working Perfectly

---

### Post by sandeepy on 2008-08-05
thanks vigyani !

---

### Post by bluegray on 2008-08-05
I'm using Gutsy and can only install empathy_0.22.0. How can I get apt-get to install the latest version? I already did a 'apt-get update'

---

### Post by zachtib on 2008-08-07
I installed the packages from this PPA, and I can hear my brother on the other end, but he can't hear me.  I know my mic is working, because I can hear myself on my end, but he's not hearing it.

Help?

EDIT: NVM, i just had to switch my input source in gnome-volume-control

---

### Post by VitaminBB on 2008-08-10
> **vigyani said:**
> Hi

Want to voice chat with Google Talk user!!
On Ubuntu 8.04 Empathy can be used to voice chat with Googletalk users.

On an updated Ubuntu 8.04; Using Synaptic Package Manager add the following third party repository and install the packages given below.

Instructions:
System --> Administration --> Synaptic Package Manager

Go to Settings->Repositories
Go to Third Party Software --> Add;
Enter the following line in APT line:

 ```
 deb http://ppa.launchpad.net/telepathy/ubuntu hardy main 
```

Close and Reload

Search and mark the following packages for install:
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

and Apply i.e. install.

Use the latest packages as older packages do not allow Gtalk/Jingle VOIP.

Cheers

References:

[LIST=1]
[*][https://launchpad.net/~telepathy/+archive]("https://launchpad.net/%7Etelepathy/+archive")
[*][http://ubuntuforums.org/showpost.php?p=4852798&postcount=21](http://ubuntuforums.org/showpost.php?p=4852798&postcount=21)
[/LIST]

**What about adding MSN or Yahoo functionality to Empathy?**

The Empathy site is terrible for info btw, they dont tell you anwhere how to get the MSN or Yahoo protocols, I dont even know if Yahoo is even supported, they only even briefly mention MSN.

And Empathy is being put forward as a future replacement for Pidgin?!

Im trying to switch over to a multi-chat account program since Pidgin cant figure out the sound screw ups it constantly causes, so im ditching Pidgin and looking for an alternative.

Why is it linux software always seems to be made by some stoner programmer in his moms basement? oh wait, I think I know *L*

---

### Post by schristo on 2008-08-11
> **VitaminBB said:**
> **What about adding MSN or Yahoo functionality to Empathy?**

The Empathy site is terrible for info btw, they dont tell you anwhere how to get the MSN or Yahoo protocols, I dont even know if Yahoo is even supported, they only even briefly mention MSN.

And Empathy is being put forward as a future replacement for Pidgin?!

Im trying to switch over to a multi-chat account program since Pidgin cant figure out the sound screw ups it constantly causes, so im ditching Pidgin and looking for an alternative.

Why is it linux software always seems to be made by some stoner programmer in his moms basement? oh wait, I think I know *L*

You need telepathy-butterfly and python-msn in order to connect to MSN. I do not use Yahoo, so I cannot help you with that.

---

### Post by bluegray on 2008-08-13
I think I got it working. Can anyone help me to test? I don't have any Gtalk contacts with a mic setup

---

### Post by VitaminBB on 2008-08-18
> **schristo said:**
> You need telepathy-butterfly and python-msn in order to connect to MSN. I do not use Yahoo, so I cannot help you with that.

Your talking another language ...

Where do I get telepathy-butterfly? how do I install it? I dont see that or python-msn on synaptic, wtf?!?

---

### Post by sergiom99 on 2008-08-18
if you enabled the repos needed to install empathy, those packages should be there. Try:
```
sudo apt-get install telepathy-butterfly python-msn
```

---

### Post by sles on 2008-09-12
Hello!

We tried to start empathy on 2 computers.
If we use account local jabber server we can call each other, but there is no connection-
I see call and then we see "connecting".
If we use gtalk accounts- all is OK.

Does server have to support something for voip support?

btw, we use ejabberd

---

### Post by Ramaddan on 2008-11-04
Hi

I'm using Empathy 2.24 through the > deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main repository

All is updated and upgraded.

Even though I have tried many things for a very long time now, and have been trying Empathy since its inception, I have never managed to get any voice to work.

Currently, I see the call button, but it's greyed out, and nothing I do can get to change, and I even tried installing on other machines with the same issue.

I even went as far as compiling myself, and enabling voice with the --enable-voip option, and still nothing.

All required packages are installed just by choosing to install > telepathy-gnome in synaptic, such as telepathy-stream-engine, telepathy-mission-control, etc...

Did anyone manage to get this working?

Am I missing something?

Can it be due to it not supporting my soundcard which is an onboard integrated soundcard?

I tried it on both Intrepid and Hardy with the same result.

Thanks

---

### Post by xtracool_protik on 2008-11-09
Hi I installed empathy and trying it for different things.
I even configured the repository [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu)
However I can't get sound working
I see the mic icon in front of contact however when I try to call nothing and the window says ringing but user can't actually get the ring. And when I get the call it just says disconnected :confused: 
I can't figure out the problem I've install all the possible plugins of empathy. I guess I'll try kopete for yahoo and will search something for gtalk. I'll update this post if I can find something.

---

### Post by WhiteHorse on 2008-11-12
Same problem here. I did get MSN, Yahoo, and Gtalk working(at least to login). Since I don't have any friends I can't really test the chat or voice. Right now I'm stuck setting up SIP accounts. They all fail with "No error provided". The only thing I can find is that mission control(MC) is not running when I run empathy from the command line:
$ empathy
** (empathy:8097): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:8097): DEBUG: mission_control_get_presence_message_actual: MC not running.
** (empathy:8097): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:8097): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:8097): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:8097): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:8097): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:8097): DEBUG: mission_control_get_connection_status: MC not running.
Any ideas as to why I can't get SIP working? All my accounts work fine in Ekiga and connect with no probs, only empathy can't connect. My version is 2.24.0
](*,)

---

### Post by dafrabbit on 2008-11-12
Same here - just dist-upgraded to Intrepid with no issues. Installed empathy as I wanted to try out whether I could get rid of skype (skype has issues with spiking my CPU when video is enabled). Can login to my gmail account no problem, text chat fine with friends, but unfortunately cannot call anyone.

If I start the call, other user accepts, but then the call window hangs at "Connecting", and after a while times out and ends the call. If other user starts the call, I will get a message prompting me to accept, but as soon as I accept, the call fails.

Anyone have any ideas? I am on newest Intrepid with Empathy 2.24.1

---

### Post by ElevenWarrior on 2008-11-21
okay I've isntalled all the packages and empathy, i go to sign in, I can't because gtalk isn't on the list of protocols. everything else is there but that one! AGHH!!!!!!!!:confused::mad::( 
any help is apericated!

---

### Post by sergiom99 on 2008-11-22
make sure all the packages listed in the first posts are installed.
Then, when you start empathy, go to 'add account' and choose 'google talk'

---

### Post by yochaigal on 2008-11-22
Installed empathy.

I can connect and chat as with pidgin but I can't call anyone (it's grayed out).  I have 2.24.1.

thanks

---

### Post by sergiom99 on 2008-11-23
@yochaigal: used to happen to me. it was related to the webcam.
please check this bug for more info about how to solve it. it was lucky to solve it without actually knowing what was i doing:
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)

---

### Post by ElevenWarrior on 2008-11-29
I did! the package I need for empathy install but Google talk isn't on the list!

---

### Post by brouhaha on 2009-02-04
Hi All,

I'm reopening an old discussion. I followed the steps mentioned in the first post on this thread. I can initiate voice calls with my friends by clicking on the mic icon. But as soon as they accept my call at their end, my voice chat window greys out and status says "closed" where is previously said "ringing".

My wife has already sounded dissent, wants me to install windows. I won't be able to resist her for long. Please help!

Namit

PS: I observe that launchpad site ([https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)) says PPA for telepathy is 
 deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) hardy main
In the first post, vigyani mentioned
 deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main
Note the missing "ppa" between /telepathy/../ubuntu
Is vigyani's post too old? Is the difference alright? Or are these two different packages (which means i shouldn't bother)?

---

### Post by Ramaddan on 2009-02-04
Hi Brouhaha,

Exactly which version of Ubuntu are you using?

---

### Post by brouhaha on 2009-02-05
> **Ramaddan said:**
> Hi Brouhaha,

Exactly which version of Ubuntu are you using?

Hey Ramaddan, I'm on Hardy - the pre-installed version being shipped by Dell.

---

### Post by Ramaddan on 2009-02-06
Hi Brouhaha,

since I am not using Hardy anymore, I am limited in what I can do, as there are some important differences between Hardy and Intrepid.

First, use this repo:
> deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) hardy main

Second, go to this link:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x638ABCA0FA3A1271]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x638ABCA0FA3A1271")

Copy everything from the begining of this sentence:
> -----BEGIN PGP PUBLIC KEY BLOCK-----
to the end of this sentence:
> -----END PGP PUBLIC KEY BLOCK-----
into a file called temp.gpg on your desktop

In Software Sources, go to the Authentication tab and import key.

Choose the file you made on the desktop to import.

This will add the signature key of the repo above to apt, and it sometimes makes more packages available, and stops some authentication errors from showing.

Now choose update in update manager, and update whatever that needs to be updated.

Make sure the following is installed in Synaptec:
> telepathy-gnome

Make sure that all _recommended_ and _suggested_ packages for the **empathy** package is installed.

After everything is installed, try empathy and tell me how everything goes.

---

### Post by brouhaha on 2009-02-06
Thanks a lot for your help Ramaddan, but I'm afraid we've only made marginal progress. Here's what I did:
[LIST=1]
[*]Uninstalled empathy
[*]uncheck the previous (vigyani's) PPA from "software sources"
[*]followed your suggestions
[/LIST]

Selecting 
```
telepathy-gnome
```
automatically got empathy 2.24.1 for me. I checked for details of empathy package at [http://packages.ubuntu.com/hardy/empathy](http://packages.ubuntu.com/hardy/empathy), there were following differences in the packages listed the vs. those on my system:
[LIST]
[*]Listed: libempathy11, Installed: libempathy14
[*]Listed: libempathy-gtk11, Installed: libempathy-gtk15
[/LIST]
I'm not sure what difference that makes, and these packages are listed on the right hand column "similar packages" in the aboce link.

Now for the marginal progress. Previously the situation was that I could send a voice chat request to friends, but as soon as they would accept it the status would turn from "ringing" to "closed", and my webcam would go black. Now, that doesn't happen anymore: my status goes to "connecting", my friends see "connected" but we can't hear or see each other. Then it closes in a few seconds. (If you call this progress)

When my friends send me a chat request, it closes down as soon as I click "accept". The windows becomes all grey.

Another interesting thing that happened while downloading the package was that although I got the public key, when I selected these packages some of them could not be authenticated by synaptic (see attached picture).

Hope this helps you help me.

---

### Post by sergiom99 on 2009-02-06
> **brouhaha said:**
> 
When my friends send me a chat request, it closes down as soon as I click "accept". The windows becomes all grey.

Sort of same thing happened to me.
Check how I kindda solved it:
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)

It has something to do with video drivers.

---

### Post by brouhaha on 2009-02-07
> **sergiom99 said:**
> It has something to do with video drivers.

Thanks for the suggestion, Sergio. I saw the link and checked that out of luvcview, dov4l, v4l-conf and cheese I only have cheese installed on my system. I don't mind going ahead and getting the rest, but I'm not convinced that there is a problem with video drivers. The reason is that when I send a voice chat request to a friend my webcam starts up (while waiting for my friend to respond).

So it just seems to me that there isn't a problem with my webcam. Is there a way to confirm it? Also, is it possible that installing these packages will start interfering with existing libraries and end up breaking things?

Thanks for all the help.

---

### Post by brouhaha on 2009-02-08
I forgot to mention that the output of the command:

```
gconftool-2 -g /system/gstreamer/0.10/default/videosrc
```

was v4l2src - same as that for sergiom.

---

### Post by sergiom99 on 2009-02-08
maybe you can file a bug and try to get some help from the project's people.
I have no idea if installing those packages you might end up breaking something else.

I'd go ahead and try it, and if they don't work, then remove them.
I didnt had a prob with video either, but so it turned out.

---

### Post by brouhaha on 2009-02-09
Hey sergio, I tried it. Nothing's improved. This time, an incoming request from a friend closes down even before I click "accept". The option to "reject/accept" flashes on the monitor for a fraction of a second and then the window greys out.

By filing a bug report do you mean at the launchpad/ubuntu or at bugzilla.gnome?

Thanks!

---

### Post by sergiom99 on 2009-02-09
At bugzilla.gome, in the projects bug tracker.
Sorry it didn't work out.

---

### Post by jerzy76 on 2009-02-13
I had the same problem.
Solved it trying different settings in **Multimedia Systems Selection** (gstreamer-properties)
In Tab video, Default Input I selected plugin **v4l** and in the section device I selected my camera, Pixart.  
All tests passed.

After that in
**System->Prefences->Sound**
I tried different settings in Tab "Devices". Finally I selected my on-board sound device (NVidia CK8 in my case), all tests passed
Finally, I unchecked "Enable software sound mixing".

After that everything, voice and video, was good with googletalk.

Here are the screenshots of my settings.

---

### Post by himanshuprakash on 2009-02-23
Hi Vigyani,
really thanks to you for beautiful sure shot for voice/vedio chat client. though i've not tested yet. But hopefully it will...



> **vigyani said:**
> Hi

Want to voice chat with Google Talk user!!
On Ubuntu 8.04 Empathy can be used to voice chat with Googletalk users.

On an updated Ubuntu 8.04; Using Synaptic Package Manager add the following third party repository and install the packages given below.

Instructions:
System --> Administration --> Synaptic Package Manager

Go to Settings->Repositories
Go to Third Party Software --> Add;
Enter the following line in APT line:

 ```
 deb http://ppa.launchpad.net/telepathy/ubuntu hardy main 
```

Close and Reload

Search and mark the following packages for install:
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

and Apply i.e. install.

Use the latest packages as older packages do not allow Gtalk/Jingle VOIP.

After installing start Empathy (Applications --> Internet --> Empathy Instant Messenger)

Configure your gmail account.

Cheers

References:

[LIST=1]
[*][https://launchpad.net/~telepathy/+archive]("https://launchpad.net/%7Etelepathy/+archive")
[*][http://ubuntuforums.org/showpost.php?p=4852798&postcount=21](http://ubuntuforums.org/showpost.php?p=4852798&postcount=21)
[/LIST]

---

### Post by mirko_3 on 2009-03-03
himanshuprakash, did that solve it for you? I'm experiencing the same problem...

---

### Post by vigyani on 2009-03-08
> **mirko_3 said:**
> himanshuprakash, did that solve it for you? I'm experiencing the same problem...

Can you please post the problems you are experiencing and the details of your distribution?

---

### Post by brouhaha on 2009-04-02
hey jerzy76,

thanks a lot for your suggestion. i happened to see this very late but it's working for me now. my friends still can't see (and therefore accept) my video invitation, but voice works.

yipee!!


> **jerzy76 said:**
> I had the same problem.
Solved it trying different settings in **Multimedia Systems Selection** (gstreamer-properties)
In Tab video, Default Input I selected plugin **v4l** and in the section device I selected my camera, Pixart.  
All tests passed.

After that in
**System->Prefences->Sound**
I tried different settings in Tab "Devices". Finally I selected my on-board sound device (NVidia CK8 in my case), all tests passed
Finally, I unchecked "Enable software sound mixing".

After that everything, voice and video, was good with googletalk.

Here are the screenshots of my settings.

---

### Post by jARLAXL on 2009-04-04
Hello all!

Also installed empathy in intrepid using the following command:
```
sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn

```

but i have this problem:
When i call another gtalk user (also installed empathy with the same procedure in intrepid) my voice appears distorted to that user but i can listen perfectly. When that user is calling me then i hear the incoming voice distorted but i am heard perfectly.

Any clues :confused:?

---

### Post by brijeshchauhan on 2009-04-25
I installed it perfectly. Everything works fine as expected on ubuntu 8.10

But my only concern is the voice quality. I dont hear other person's voice clearly. Gtalk on windows has excellent voice quality. Is there anything that can be done to solve this?

---

### Post by vigyani on 2009-05-02
> **brijeshchauhan said:**
> I installed it perfectly. Everything works fine as expected on ubuntu 8.10

But my only concern is the voice quality. I dont hear other person's voice clearly. Gtalk on windows has excellent voice quality. Is there anything that can be done to solve this?

Hi

I have been using it on Hardy i.e. 8.04, voice quality is good. Please check you audio device and tweak volume settings and see it you get better voice quality.

regards
Vig.:guitar:

---

### Post by rajan on 2009-05-14
after about 2 weeks of struggling, reading everything that was online about empathy and gtalk, i finally got this to work. 2 things that helped me:

1. this excellent, simple guide by vigyani

2. updating EVERYTHING. initially empathy did not work for me: i could not hear people, and i could not answer phone calls (nor could i place them). i could chat (via keyboard) though, but i can do that on gmail's web interface. in order to get the voice chat working, i went through synaptic and reinstalled or upgraded every package that vigyani listed in his first post:

> 

Search and mark the following packages for install:
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine



after this, i updated my system, as a whole.


last thing i would say to people having problems with this is to read the whole thread. it's long, but helpful. 

here's a few details of my system:

```

rajan@paravati:~$ lsusb 
--cut--
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
--cut--

rajan@paravati:~$ uname -a
Linux paravati 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux

rajan@paravati:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy


```

---

### Post by sergiom99 on 2009-05-24
I upgraded to Kubuntu JJ (fresh install) but I still cannot be heard and I can clearly hear the other party involved.

---

### Post by Sunrise on 2009-05-28
Hi,

I have installed empathy 2.24.1 on hardy perfectly, but there is problem with sound which was mentioned earlier here by some others.

I can hear my brother`s voice, but he can not hear me (sometimes, vice versa, depends on who calls first). I accidentally found simple remedy for that. Each time I want to hear my brother`s voice, I should *[COLOR="Red"]mute[/COLOR]* my Mic! and if I want to speak, I should unmute it again, Something like talkie-walkie toys with just *one* direction connection in a moment.

How can I adjust sound settings to get rid of this boring mute-unmute process in voice chat with empathy?

---

### Post by irha on 2009-06-07
I got empathy 2.26.1 to install using synaptic and it found and imported my pidgin accounts. I enabled just the gmail a/c and it was able to login (to double check, when I purposefully gave a wrong password, I got an error as expected). However, I don't see any of my contacts. If I try to initiate a chat anyway, the messages don't reach the destination. I am running pidgin in parallel with this gmail a/c as well as another dummy a/c. If I chat from the main a/c to the dummy a/c from pidgin, I can see the messages reaching back to pidgin, but when I chat from the dummy a/c to the main a/c, they only reach pidgin, not empathy (though my status shows online). Similarly, when I chat from main a/c to dummy a/c in empathy, I expect those messages to reach pidgin. Any help on understanding what is wrong with my empathy setup will be appreciated.
__

---

### Post by dael99 on 2009-06-09
using 2.27.2 and nothing happens, using GMAIL, i see my contacts but i can't use mic or webcam....

---

### Post by rajan on 2009-06-10
I just installed a few of the "upgrades" that ubuntu told me i needed to install urgently and one of them caused my voice chat to stop working. has anyone else had this happen? it was previously working fine (see 4 posts previous to this one), but now my relatives cannot hear me, even though I can hear them. also, skype works fine, as usual.

---

### Post by Sunrise on 2009-06-10
> **rajan said:**
> I just installed a few of the "upgrades" that ubuntu told me i needed to install urgently and one of them caused my voice chat to stop working. has anyone else had this happen? it was previously working fine (see 4 posts previous to this one), but now my relatives cannot hear me, even though I can hear them. also, skype works fine, as usual.

Rajan: maybe you have my problem (see #81). If it is the case, ask your relatives to mute Mic which allow you to speak. It seems strange, but works for me!

---

### Post by rajan on 2009-06-10
> **Sunrise said:**
> ....ask your relatives to mute Mic which allow you to speak. It seems strange, but works for me!

oh.... i see what you were saying. I thought you meant that I should mute the mic on my side (the linux side). I was trying to find the mute button for a while without luck #-o 

I'll see if that works, and maybe I can do some research on this during my upcoming vacation. thanks for the reply, Sunrise.

---

### Post by irha on 2009-06-11
> **dael99 said:**
> using 2.27.2 and nothing happens, using GMAIL, i see my contacts but i can't use mic or webcam....
I now have the same situation. After I checked "Encryption required" under Advanced settings, I suddenly got my contacts loaded and I can now see their status changes etc., but I can't initiate voice or video chat.

Update: Seems like the mic button appears only if the other party has the capability to do voice chat (which makes sense). Since I was logged in through pidgin for the test account, I didn't get any mic icon, but when I logged in through google talk native client, I was able to initiate a voice call. However, I couldn't conclude that voice is actually working, though there was echo due to the fact that both laptops were close to each other (indicating some feedback). After I hung up the call, the ubuntu netbook had a constant noise coming from its speaker as if empathy left some sort of stream open. Even after quitting most applications, including empathy, the noise didn't die down. I initiated a shutdown and only half way through the process it suddenly became silent. Also, when I logged in using google chat browser plugin, I expected the video to work, but it didn't. Empathy seemed to think correctly that the other party has video, but the google browser plugin clearly indicated that the empathy side didn't have video.

---

### Post by irha on 2009-06-11
I am in a worse situation now. The noise that I observed before is actually happening all the time now (even after a reboot) and all applications that use sound are failing. Skype worked flawlessly before, but now a test call itself fails with the error "problem with audio playback". I went into sound preferences and tried testing the devices one by one. All of them worked except for the "Sound capture" under "Audio Conferencing" which had it set to "ALSA". I tried other options but none of them worked. Any help is appreciated. I could try uninstalling empathy, but I am afraid it will leave a bunch of packages behind including the one causing the problem.

---

### Post by rajan on 2009-06-12
> **irha said:**
> I could try uninstalling empathy, but I am afraid it will leave a bunch of packages behind including the one causing the problem.

yeah... i think uninstalling will just cause more problems. what happens when you unplug your webcam? how about your speakers?

---

### Post by irha on 2009-06-12
I am using the built-in speakers and webcam of the laptop (dell mini 9). Due to the limited time I have to resolve this issue, I restored the disk image I took a few days back before installing empathy. Though this would set me back a few days, getting audio working right now is more important to me. After the restore, Skype worked fine at first but soon I couldn't make any calls (though there is no longer noise coming from the speakers). With the help of [this]("http://www.ubuntumini.com/2009/04/skype-on-dell-mini-9.html") blog, I was able to change the audio settings and get Skype working again. Right now, I have no clue on the following:
- What caused the speakers to emit constant noise after installing and using empathy and why didn't it go away even after a logout or reboot.
- Why did sound device setting change all of a sudden to cause Skype to fail.
I took a fresh dd image of the drive and will try to install empathy and see if I can get a better result this time.
[]("http://www.ubuntumini.com/2009/04/skype-on-dell-mini-9.html")

---

### Post by hotweiss on 2009-06-25
I just installed empathy, and I don't have Empathy in my taskbar, nor do I have a tray icon.

---

### Post by alaukik.kot on 2009-08-15
hi, i have recently downloaded empathy from synaptic and also other supporting softwares along with it
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

but i'm unable to connect, my computer is connected with huge lan of my college, which is then connected to INTERNET via server( whose ip 172.31.16.10) pidgin use to work very fine with me....
can i configure my empathy, will it work... can some one please guide me... i'm really interested in starting google voice on my ubuntu...

---

### Post by amsum on 2009-09-22
I have a weird problem. I configured Ekiga in Desktop with Ubuntu 9.04. When I am calling to gTalk on my laptop with Vista, its connecting but no sound from either side. The same holds true when I am calling from my laptop to desktop. I tried even with yahoo messenger instead of gtalk and I am facing exactly same problem. Any suggestion?

I believe Ekiga is still not fully ready to voice chat with yahoo messenger/gtalk.

---

### Post by Frank-NL on 2009-10-05
It seems that I cannot connect to Google Talk with Empathy, could anybody please explain this output?

(empathy:5074): tp-fs-DEBUG: calling MediaSessionHandler::Ready
(empathy:5074): tp-fs-DEBUG: New stream, stream_id=1, media_type=0, direction=3
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding STUN server 209.85.137.126:19302
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding relay (udp) 209.85.229.126:19295 IfSYGBz2LGVnjY87:qfG4Zdd0v3drd0jg 1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding relay (tcp) 209.85.229.126:19294 IfSYGBz2LGVnjY87:qfG4Zdd0v3drd0jg 1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding relay (tls) 209.85.229.126:443 IfSYGBz2LGVnjY87:qfG4Zdd0v3drd0jg 1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding relay (udp) 209.85.229.126:19295 hyZUWiXyrkfVvpFp:RnAD9octNB3mVtdO 2
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding relay (tcp) 209.85.229.126:19294 hyZUWiXyrkfVvpFp:RnAD9octNB3mVtdO 2
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) get_all_properties_cb: Adding relay (tls) 209.85.229.126:443 hyZUWiXyrkfVvpFp:RnAD9octNB3mVtdO 2
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: called (send_local:1 send_supported:0)
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 102: audio SPEEX clock:8000 channels:1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 103: audio SPEEX clock:16000 channels:1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 96: audio SIREN clock:16000 channels:0 bitrate=16000
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 0: audio PCMU clock:8000 channels:0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 8: audio PCMA clock:8000 channels:0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 3: audio GSM clock:8000 channels:0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 99: audio telephone-event clock:16000 channels:0 events=0-15
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 100: audio telephone-event clock:8000 channels:0 events=0-15
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec SPEEX [102]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec SPEEX [103]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec SIREN [96]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec PCMU [0]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec PCMA [8]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec GSM [3]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec telephone-event [99]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) fs_codecs_to_tp: adding codec telephone-event [100]
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: calling MediaStreamHandler::Ready
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_bus_message: Codecs changed
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: called (send_local:0 send_supported:0)
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 102: audio SPEEX clock:8000 channels:1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 103: audio SPEEX clock:16000 channels:1
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 96: audio SIREN clock:16000 channels:0 bitrate=16000
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 0: audio PCMU clock:8000 channels:0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 8: audio PCMA clock:8000 channels:0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 3: audio GSM clock:8000 channels:0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 99: audio telephone-event clock:16000 channels:0 events=0-15
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) _tf_stream_try_sending_codecs: 100: audio telephone-event clock:8000 channels:0 events=0-15
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_new_local_candidate: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: called
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '192.168.1.100'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '192.168.1.100'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = 'external ip address'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = 'external ip address'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.229.126'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.229.126'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.229.126'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.229.126'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.229.126'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.229.126'
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) set_stream_playing: 0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) set_stream_sending: 0
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) add_remote_candidate: adding remote candidate R1
tp-fs-Message: tf_stream_error: stream error errorno=6 error=Invalid remote candidates passed
(empathy:5074): tp-fs-DEBUG: stream 1 0x2129a70 (audio) close: close requested by connection manager

---

### Post by vikrantsingh on 2009-10-13
hello vigyani
i did all the step that you mentioned above for using voice chat with gtalk in empathy 
but still i am unable to do voice chat in empathy..
plz help me to sort out this problem actually i am a new bee in linux..

vikrant

---

### Post by vigyani on 2009-11-02
Which distribution are you using?

I understand Ubuntu 9.10 has Empathy installed by default :D, hence you need not install it, just configure your google account.

regards
Vig 

> **vikrantsingh said:**
> hello vigyani
i did all the step that you mentioned above for using voice chat with gtalk in empathy 
but still i am unable to do voice chat in empathy..
plz help me to sort out this problem actually i am a new bee in linux..

vikrant

---

### Post by bhishan on 2010-01-10
As for video chat under linux, I found that link in a googlegroup [https://spreadsheets.google.com/view...fd2dhlZI2m_bRQ](https://spreadsheets.google.com/view...fd2dhlZI2m_bRQ) so maybe they don't forget us totally
Plus, if lots of people sign up as testers, so that they know that there are lots of people interested, maybe they'll speed up the process!

---

### Post by sergiom99 on 2010-01-11
> **bhishan said:**
> As for video chat under linux, I found that link in a googlegroup [https://spreadsheets.google.com/view...fd2dhlZI2m_bRQ](https://spreadsheets.google.com/view...fd2dhlZI2m_bRQ) so maybe they don't forget us totally
Plus, if lots of people sign up as testers, so that they know that there are lots of people interested, maybe they'll speed up the process!

Broken link...

---

### Post by bulbmaker on 2010-01-11
i recently installed ubuntu 9.10 on my hp pavilion dv6226tx laptop. i configured empathy for gmail. on first day it worked fine except video chat. next day its giving network error. i uninstalled empathy n reinstalled it, just trying luck. it didn't work, same error. plz help me. i want video chat too. cheese didn't recognize my webcam.

---

### Post by pinkpinkpinkpanther on 2010-06-06
Help, Help, Help Please.

When I call by empathy, for first 30sec everything is ok, then the other side doesn't have my voice and after 45sec I don't hear anything and after 60sec call drops!

Any idea?

---

### Post by hansum_rahul on 2010-06-14
I am also having a similar problem... on a Hardy box.

But guess the problem was because I removed my tv-tuner card. So I just changed my multimedia properties (Test Input now)... waiting for someone to come by ... so I can test it out...

---

### Post by hansum_rahul on 2010-06-14
I am having another problem with Yahoo accounts... it shows a network error?

---

### Post by YannBuntu on 2010-07-05
Dear all,
as far as I know, to do voice+video calls on Empathy with Google Talk protocol, you need :
- Empathy with [Telepathy PPA]("https://launchpad.net/~telepathy/+archive/ppa")
- the ubuntu-restricted-extras package
- and of course a Gtalk account (= Gmail address)

---

### Post by pinkpinkpinkpanther on 2010-07-10
My Problem just solved by upgrading into Ubuntu 10!

---

### Post by AldenIsZen on 2010-10-10
What do I need to do to get this to work in Ubuntu 10.10?

---

### Post by jalmado on 2010-10-17
Hi, in ubuntu 10.10 and empathy I can use the video chat with gmail account only, not with hotmail account, though it runs slowly, but I can't get the sound to work.

Does anyone know how to configure, if possible, the audio settings for empathy?

---

### Post by srose11 on 2010-10-23
Hi I want to use Yahoo Voice Call & Call Out in Ubuntu.

Linux is this available yet?

---

