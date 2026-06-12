---
title: "Record / capture streaming audio in Natty esp BBC iPlayer"
date: 2011-05-02
forum: Multimedia Software
---

### Post by BlueGene1402 on 2011-05-02
Hiya. I practically live on this site:
[http://www.bbc.co.uk/iplayer/radio](http://www.bbc.co.uk/iplayer/radio)

I used Freerecorder 4 in Windows *spits* to record the audio. It captured not only the streaming audio, but also every sound produced by my laptop. Meaning I have no problem with that - I just have to be careful not to cause any unnecessary CLICK or PING to interrupt my recording ;)

Natty - I've tried a few different applications but I can't seem to manage it. I would appreciate any help or advice. The more idiot proof the better. I am no computer geek - my nerdyness lies elsewhere.

And thank you for taking the time to consider my problem.

---

### Post by BlueGene1402 on 2011-05-08
I was kindly directed to the solution on this page:

[B]Record all audio output 
[http://ubuntuforums.org/showthread.php?t=1531367](http://ubuntuforums.org/showthread.php?t=1531367)[/B]

outRec is a nifty little application that did the trick for me :KS

---

### Post by nothingspecial on 2011-05-09
You might want to have a look at get_iplayer.

The version in the repos isn't fully functional. But the latest version is. Rather than installing all the dependencies one by one, it would be easier to do this.

Get the old version and everything it needs, plus git to get the latest version

```
sudo apt-get install get-iplayer git
```

Then get the latest version

```
git clone https://github.com/jjl/get_iplayer.git
```

Replace the old version with the new version

```
sudo mv get_iplayer /get_iplayer /usr/bin/get_iplayer
```

Now use a keyword to search for a radio program. I like the Punk show on Radio 1

```
get_iplayer --type=radio Punk
```

Wait a few minutes and get_iplayer will find all the available radio shows and give you any matches at the end. In my case


```
Matches:
[COLOR="Red"]11892[/COLOR]:	Punk Show with Mike Davies - The Lock Up stage line-up revealed!, BBC Radio 1, Experimental & New,Guidance,Music,Radio,Rock & Indie
```

It's the number at the beginning we are interested in. To download it

```
get_iplayer -g 11892
```

---

### Post by BlueGene1402 on 2011-05-09
Thanks **nothingspecial** for the instructions. I appreciate the breakdown since I don't know what I'm doing :p

It worked as a whole, but I can't get any of the programmes that I want! Hancock's Half Hour, Just A Minute..

I used your example "Punk" and it worked like a charm, found it quickly & download started with no problems.

Other stuff worked too BUT it kept finding "0 Matching Programmes" for every show that I really wanted lol!!

So it's doing it fine for some but not at all for others (e.g. Persuasion or Mansfield Park) and I don't know why.

---

### Post by nothingspecial on 2011-05-09
I'm no get_iplayer expert, just a user :P

I suspect the problem is that the instructions (--type=radio) I gave you only work for programs broadcasted in the last 7 days.

I'm pretty sure though, that get_iplayer can access anything on the iPlayer website.

It's just that I have never used it that way.

I will have a look sometime this week, but I'd appreciate it if you would too.........

........ I'll race you - "Who can download archived iPlayer radio material with get_iplayer first? BlueGene1402 or nothingspecial?"

...... There might also be a problem with the BBC7/Radio4 extra change that the get_iplayer devs have not dealt with yet.

---

### Post by ron999 on 2011-05-09
> **nothingspecial said:**
> 

...... There might also be a problem with the BBC7/Radio4 extra change that the get_iplayer devs have not dealt with yet.

Hi
The updated version at **github** hasn't been maintained since March last year.

There's a new updated script available at **infradead**.
One of the features is to cater for Radio 4 Extra.
It might solve the problem.
Information is here:- [http://git.infradead.org/get_iplayer.git]("http://git.infradead.org/get_iplayer.git")

Download:-
```
git clone git://git.infradead.org/get_iplayer.git
```
Then use new get_iplayer script to replace the one that's in usr/bin folder.

---

### Post by nothingspecial on 2011-05-09
> **ron999 said:**
> Hi
The updated version at **github** hasn't been maintained since March last year.

There's a new updated script available at **infradead**.
One of the features is to cater for Radio 4 Extra.
It might solve the problem.
Information is here:- [http://git.infradead.org/get_iplayer.git]("http://git.infradead.org/get_iplayer.git")

Download:-
```
git clone git://git.infradead.org/get_iplayer.git
```
Then use new get_iplayer script to replace the one that's in usr/bin folder.

Thanks for the info, I've updated :D

However 

```
$ get_iplayer --type=radio "Hancock"
get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.


INFO: 0 Matching Programmes
```

```
$ get_iplayer --type=radio "Just A Minute"
get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.


INFO: 0 Matching Programmes
```

Please don't take this the wrong way. Thankyou for the pointer :D

Still can't find Hancock or Just A Minute though

---

### Post by ron999 on 2011-05-09
> **nothingspecial said:**
> 
Still can't find Hancock or Just A Minute though

It's hit-and-miss using keywords.:(
Try using the PID from the show's iPlayer website page.
> [http://www.bbc.co.uk/iplayer/episode/](http://www.bbc.co.uk/iplayer/episode/)[COLOR="Red"]b008v13d[/COLOR]/Hancocks_Half_Hour_The_Sleepless_Night/

Then:-
```
get_iplayer --get --type=radio --pid=b008v13d
```

And 'Just a Minute':-
```
get_iplayer --get --type=radio --pid=b00l5zqc
```

---

### Post by nothingspecial on 2011-05-09
> **ron999 said:**
> It's hit-and-miss using keywords.:(
Try using the PID from the show's iPlayer website page.


Then:-
```
get_iplayer --get --type=radio --pid=b008v13d
```

And 'Just a Minute':-
```
get_iplayer --get --type=radio --pid=b00l5zqc
```

Thankyou.

That does it.

Have a cold one on me :P

---

### Post by BlueGene1402 on 2011-05-10
It worked brilliantly! I'll be downloading period dramas by the truckload \\:D/

I've grabbed HHH & JAM and now converting from FLV to mp3.. Thanks guys!

---

### Post by ron999 on 2011-05-10
> **BlueGene1402 said:**
> It worked brilliantly! I'll be downloading period dramas by the truckload \\:D/

I've grabbed HHH & JAM and now converting from **FLV** to mp3.. Thanks guys!

If you have downloaded **FLV** files you're doing something wrong.

---

### Post by Filthy Stockings on 2011-06-08
WED 8 JUNE 11 

Hi 
New to the forum AND to UBUNTU use [3 days] but have found GET-IPLAYER very useful.

I was curious why no BBC 4 EXTRA programmes and so found this forum and the advice to upgrade.

Copied the link

[http://git.infradead.org/get_iplayer.git](http://git.infradead.org/get_iplayer.git) but could not see any obvious DOWNLOAD tab [sorry but am not well educated in IT]

so copied the "DOWNLOAD CODE" link also given by the same poster

git clone git://git.infradead.org/get_iplayer.git  
and found a highlighted DOWNLOAD option 

download[aur-f6e08d0106045048e9bb46118318b185203174c8.tar.xz]("http://pkgbuild.com/git/aur.git/snapshot/aur-f6e08d0106045048e9bb46118318b185203174c8.tar.xz")

though that didn't seem to clearly state it was GET-IPLAYER. BUT downloaded it anyway; quite a large file and can't seem to find it.

Am I doing the right thing or could someone advise further?

All I want is the modified GET-IPLAYER which allows 4 EXTRA radio programmes to be downloaded.

Thanks in advance.

SA UK

---

### Post by nothingspecial on 2011-06-08
Open a terminal. Press Ctrl-Alt-T (at the same time)

Copy and paste these lines one at a time

```
sudo apt-get install git
```

```
git clone git://git.infradead.org/get_iplayer.git
```

```
sudo rm /usr/bin/get_iplayer
```

```
sudo mv get_iplayer/get_iplayer /usr/bin/
```

And you should be good to go.

---

### Post by Filthy Stockings on 2011-06-08
Thanks for the hasty reply.

Am feeling very thick, though.

Do I paste those code lines in ONE AT A TIME and then press ENTER? or just one SPACEBAR click?

Tried both options but only got this

[SIZE=3][I]ubuntu@PC-3:~$ sudo apt-get install  git git clone git://git.infradead.org/get_iplayer.git sudo rm /usr/bin/get_iplayer sudo mv get_iplayer/get_iplayer /usr/bin/
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package clone
E: Unable to locate package git://git.infradead.org
E: Couldn't find any package by regex 'git://git.infradead.org'
E: Unable to locate package rm
E: Unable to locate package /usr/bin
E: Unable to locate package mv
E: Unable to locate package get_iplayer
E: Unable to locate package /usr/bin
ubuntu@PC-3:~$ 

[/I][SIZE=2]LINUX really is a new language I'm afraid.

Would ask my PC builder but he's away and a bit desperate to catch HHH;PICNIC before it vanishes.

Can you help me further please; ta very much.

SA

[/SIZE][/SIZE]

---

### Post by nothingspecial on 2011-06-08
Paste the first one, then press enter.

Then the second one and then press enter etc etc

When it asks for your password you won't see it as it is typed.

---

### Post by Filthy Stockings on 2011-06-08
Ta v much. Will have another go

SA

---

### Post by Filthy Stockings on 2011-06-08
Am like a bad penny..............

Did as you advised, pasted 1st link and ENTER then got the [sudo] password thing so just ENTERed again [DIDN'T ENTER MY PASSWORD....SHOULD I HAVE?] and some code lines ran then got the option to continue y/n so typed y and ENTER.

Then was back to the usual terminal initial code [AS USED TO SEEING AFTER FEW DAYS OF GETIngIPLAYTER] so started to paste the remaining code lines you gave and pressed ENTER after each. 

AND the TERMINAL looks like this....

[SIZE=3]ubuntu@PC-3:~$ sudo apt-get install git
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  emacsen-common git-man liberror-perl
Suggested packages:
  git-doc git-el git-arch git-cvs git-svn git-email git-daemon-run git-gui
  gitk gitweb
The following NEW packages will be installed:
  emacsen-common git git-man liberror-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,278 kB of archives.
After this operation, 12.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main emacsen-common all 1.4.19ubuntu2 [17.7 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main liberror-perl all 0.17-1 [23.8 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main git-man all 1:1.7.4.1-3 [579 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main git amd64 1:1.7.4.1-3 [4,658 kB]
Fetched 5,278 kB in 15s (336 kB/s)                                             
Selecting previously deselected package emacsen-common.
(Reading database ... 140224 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu2_all.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.4.1-3_all.deb) ...
Selecting previously deselected package git.
Unpacking git (from .../git_1%3a1.7.4.1-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up emacsen-common (1.4.19ubuntu2) ...
emacsen-common: Handling install of emacsen flavor emacs
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.4.1-3) ...
Setting up git (1:1.7.4.1-3) ...
ubuntu@PC-3:~$ git clone git://git.infradead.org/get_iplayer.git
Cloning into get_iplayer...
remote: Counting objects: 1797, done.
remote: Compressing objects: 100% (456/456), done.
remote: Total 1797 (delta 1319), reused 1797 (delta 1319)
Receiving objects: 100% (1797/1797), 1.14 MiB | 277 KiB/s, done.
Resolving deltas: 100% (1319/1319), done.
ubuntu@PC-3:~$ sudo rm /usr/bin/get_iplayer
ubuntu@PC-3:~$ sudo mv get_iplayer/get_iplayer /usr/bin/
ubuntu@PC-3:~$ 

[SIZE=2]So did I do done right, dya think?

Just checked my HOME FOLDER and can see a GET-IPLAYER folder, which wasn't sure if there before but can't see any date on PROPERTIES to ascertain if that true.
[/SIZE]
Ulp................?

[/SIZE]

---

### Post by nothingspecial on 2011-06-08
Yeah, you've done it right. Now see if you can access any radio4 extra stuff.

---

### Post by nothingspecial on 2011-06-08
Try (in the terminal again)

```
get_iplayer --type=radio hancock
```

---

### Post by Filthy Stockings on 2011-06-08
HOORAH!! Yup, whilst I was refreshing this site rapidly I also found time to do a usual --radio=type and LO UND BEHOLD........there were the beauties....

Hancock/Ed Reardon and G Keillor............well chuffed.

THANKS SO MUCH.

My PC builder will be chuffed that have followed his "give em a rod and they'll learn to fish" approach; he said there was help out there online.

BRILLIANT!!!

---

### Post by nothingspecial on 2011-06-08
No problem :popcorn:

---

### Post by shantiq on 2011-06-09
ok for detailed instructions on using get-iplayer
You may already know all this :KS:KS


for radio and tv
simply enter the ```
get-iplayer
``` command in terminal then you have a list of all the programs  
First the most recent ones are listed under ADDED then come the others ones currently available




  find the code number you want then use the ```
--g  number you want
```


so for example 

```
get-iplayer  --g 835  --vmode=flashvhigh2
```

this for a tv program   ```
--vmode=
``` stands for video mode


if it is a radio program you want   ```
--mode=
``` is what you want

instead of --g   you can go to BBC page and copy the url address of program you want then you use ```
--pid=
```  instead of ```
--g
```


[B]EXAMPLES
========[/B]

> 
get_iplayer --mode=flashaacstd --pid=http://www.bbc.co.uk/iplayer/console/b00npls6


copies a radio program i got the address of from the site itself


this here for tv

> get-iplayer --pid=http://www.bbc.co.uk/iplayer/episode/b00qpm4c/Latin_Music_USA_Borderlands/   --vmode=flashvhigh2



if you cannot get what you want

try the test function to see which versions are available


> get-iplayer --pid=http://www.bbc.co.uk/iplayer/episode/b00qpm4c/Latin_Music_USA_Borderlands/  [COLOR="Red"] --test[/COLOR]

for radio ```
flashaachigh,flashaacstd,flashaudio,realaudio,flashaa&#8208;
              clow
```

for tv   ```
flashhigh; flashhigh2; flashvhigh; flashvhigh2; flashhd
```

]

then you will know which versions are there they change that all the time!!

---

### Post by shantiq on 2011-06-09
> **ron999 said:**
> If you have downloaded **FLV** files you're doing something wrong.


i am not sure there Ron sometimes you get flv sometimes mp4
i have had  all  combinations


they love changing it all around it seems:KS:KS:KS

---

### Post by Filthy Stockings on 2011-06-15
Ta for further advice/options.

HOWEVER. I have noticed that since I updated my GETIPLAYER to list the RADIO 4 EXTRA progs, that all subsequent radio downloads then play with a full screen STATIC image, which looks like the one that might be on the original IPLYR page, but enlarged and distorted.

Previous to updating to get EXTRA, all radio d/l'd and then played, automatically allowed the player's animations to run; which I prefer.

Any advice, to a novice, I'm afraid, as to if I can convert all my BBC d/ls to allow the 'player animations' and NOT the static distorted prog-related image?

Thanks

SA

---

### Post by ron999 on 2011-06-15
> **Shia Asininity said:**
>  since I updated my GETIPLAYER to list the RADIO 4 EXTRA progs, that all subsequent radio downloads then play with a full screen STATIC image, which looks like the one that might be on the original IPLYR page
Hi
The STATIC image that you see is the 'cover art' thumbnail from the iPlayer website.
Verify this using command:-
```
AtomicParsley *filename*.m4a -t
```
You will probably see one line that says:-
**Atom "covr" contains: 1 piece of artwork**

To delete the artwork use a command like this:-
```
AtomicParsley *filename*.m4a --artwork REMOVE_ALL --overWrite
```

---

### Post by Filthy Stockings on 2011-06-16
THU 16/6 Sorry for late reply and ta for info.

As stated, am a novice so bear with me, with regards to entering that code to remove the STATIC image, can I only do that once I have DL'd the programme and all the code is still visisble in the TERMINAL?

I tried it on a previously DL'd prog but in my HOME FOLDER that prog just had its own original BBC IPLAYR code and entering that in a NEW TERMINAL just produced a NOT RECOGNISED response.

Can it be done once I have closed the original POST D/L TERMINAL, with all its displayed code.........or is it too late for all the progs I have DL'd since adapting my original PC loaded GET-IPLAYR prog, to add 4EXTRA progs to the list?

Have just DL'd a radio prog and with the DL completed and the TERMINAL showing all the data I then tried the code you gave to determine if the STATIC IMAGE is recognised, as you suggested.

It gave this reply 

"ubuntu@PC-3:~$ AtomicParsley **11569**.m4a -t
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open 11569.m4a for reading: No such file or directory
ubuntu@PC-3:~$ "

I entered the current GET-IPLAYER numerical prog reference...........IS THAT THE FILENAME you advised me to enter OR is there somewhere else I can find the CORRECT filename so the -t aspect functions, as you suggested?

Hope the above makes sense............thanks in advance.

SA

---

### Post by Filthy Stockings on 2011-06-16
AH!! I searched up to the top of the JUST DL'd radio prog TERMINAL and DID FIND a FILENAME line so copied that into the code you gave and GOT A RESULT as you indicated.

BUT when I entered the code you gave to REMOVE_ALL ARTWORK it got me this response.

"Atom "covr" contains: 1 piece of artwork
ubuntu@PC-3:~$ AtomicParsley Marc_Riley_-_Tuneyards_b011rb00_default.m4a --artwork REMOVE_ALL  --overwrite
AtomicParsley: unrecognized option '--overwrite'"

Did I make an enter ERROR? Can't see where BUT least now know can find the ARTWORK line of code.....though only on the freshly DL'd TERMINAL. 

Is that same FILENAME visible somewhere in the past DL'd progs? If so can you direct me how to find it, please?

Thanks again.

---

### Post by Filthy Stockings on 2011-06-16
AH AH! Noted that I entered overwrite instead of over**W**rite and that has WORKED to remove the annoying COVER ART.

BUT tried the same on a PREVIOUSLY DL'd radio prog, checked PROPERTIES to find what seemed like, a FILENAME highlighted, copiy/pasted it and tried to REMOVE_ALL artwork....but THAT filename was not recognised.

It did look a bit LONG ie

"
[I]ubuntu@PC-3:~$ AtomicParsley Bob_Harris_Sunday_-_Nils_Lofgren_and_Mostly_Autumn_are_live_plus_Loudon_Wainwright_III_and_Lucy_Wainwright_Roche_are_in_session_b011lgxl_default.m4a --artwork REMOVE_ALL --overWrite
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open Bob_Harris_Sunday_-_Nils_Lofgren_and_Mostly_Autumn_are_live_plus_Loudon_Wainwright_III_and_Lucy_Wainwright_Roche_are_in_session_b011lgxl_default.m4a for reading: No such file or directory
[/I]
SO tried to shorten the FILENAME to just the prog identity code 

b011lgxl_default.m4a

BUT that wasn't recognised either ie

[I]ubuntu@PC-3:~$ AtomicParsley _b011lgxl_default.m4a --artwork REMOVE_ALL --overWrite
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open _b011lgxl_default.m4a for reading: No such file or directory[/I]

SO have at least found what to do AS SOON as I have DL'd a radio prog BUT still ignorant of what to do with the several I DL'd over the last week.

ANY advice from ANYONE greatly appreciated.

Thanks

SA

---

### Post by Filthy Stockings on 2011-06-16
Have to get away so last posting til evening BUT have found ODD experience.

ie

When entered this, for a prog DL;d TODAY but after had, mistakenly, CLOSED THE 'DL' TERMINAL, got result and ARTWORK REMOVED

ubuntu@PC-3:~$ AtomicParsley Gideon_Coe_-_09_06_2011_b011rb0g_default.m4a --artwork REMOVE_ALL --overWrite

 Updating metadata... ubuntu@PC-3:~$ 

WHEN tried to do same for prog DL'd 2 days ago got this

ubuntu@PC-3:~$ AtomicParsley Gideon_Coe_-_06_06_2011_b011r3pf_default.m4a --artwork REMOVE_ALL --overWrite
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open Gideon_Coe_-_06_06_2011_b011r3pf_default.m4a for reading: No such file or directory

As can be seen, the filenames for EACH of the two attempts are nearly indentical, I have not omitted anything and YET the 2nd one would NOT WORK.

Is there a TIME LIMIT on when ARTWORK can be removed, do you think?

Thanks for any future help. Can log back in later.

SA

---

### Post by nothingspecial on 2011-06-16
You've got some good radio shows there.

I'm guessing that you have moved the items you downloaded 2 days ago to another folder. In which case you need to tell the terminal which one.

Now, if the folder you have moved them to is called Radio you would have to specify that followed by a / before the file, so

```
AtomicParsley [COLOR="Red"]Radio/[/COLOR]Gideon_Coe_-_06_06_2011_b011r3pf_default.m4a --artwork REMOVE_ALL --overWrite
```

---

### Post by Filthy Stockings on 2011-06-17
FRI 17 6 11
Thanks for replying.

Have tried your suggestion but no luck

  	 	 	 	 	 	   [SIZE=2]ubuntu@PC-3:~$ AtomicParsley ubuntu/radio/Down_the_Line_Series_2_-_Episode_4_b011ppnl_default.m4a --artwork REMOVE_ALL --overWrite [/SIZE]
[SIZE=2] [/SIZE][SIZE=2] AP error trying to fopen: No such file or directory [/SIZE]
[SIZE=2] [/SIZE][SIZE=2] AtomicParsley error: can't open ubuntu/radio/Down_the_Line_Series_2_-_Episode_4_b011ppnl_default.m4a for reading: No such file or directory [/SIZE]
[SIZE=2] [/SIZE][SIZE=2] ubuntu@PC-3:~$  [/SIZE]
[SIZE=2] [/SIZE]
firstly tried to just add "radio" as that's where I store the progs.

That failed so added my HOME folder "ubuntu" but no luck neither.

No big problem as, thanks to advice here, I now find that if I AtomicParsley when the DL'd prog terminal is up, I get the desired effect.....no blurry foto and thus the option to have swirling fractals to accompany the laughs and tunes and drama...and 'learning' that BBC radio put out in such abundance.

The beauty with now being LINUX'd and able to DL rather than streaming, is can 'slider' out the irritating trails AND PRESENTERS that ruin the listening pleasure.

That was possible whilst streaming, for years, til BBC/SIEMENS fixed the NOT-BROKEN IPLAYER system and ruined simple 'slidering'.

Good luck with your endeavours and thanks for the interest and assistance.

Was told the LINUX users would be helpful and so far so impressed.

SA

---

### Post by ron999 on 2011-06-17
> **Shia Asininity said:**
> 
firstly tried to just add "radio" as that's where I store the progs.

That failed so added my HOME folder "ubuntu" but no luck neither.


Hi Shia
That's not correct.

Do this:-
**RIGHT-CLICK** on the file.
Then **COPY**.
Then **PASTE** it into a text editor.

It will look something like this:-
**/home/ron/radio/The_Complete_Smiley_-_Tinker_Tailor_Soldier_Spy_Part_3_b011pq1v_default.m4a**

So my command would be:-
```
AtomicParsley /home/ron/radio/The_Complete_Smiley_-_Tinker_Tailor_Soldier_Spy_Part_3_b011pq1v_default.m4a --artwork REMOVE_ALL --overWrite

```

> ron@ubuntu:~$ AtomicParsley /home/ron/radio/The_Complete_Smiley_-_Tinker_Tailor_Soldier_Spy_Part_3_b011pq1v_default.m4a --artwork REMOVE_ALL --overWrite

 Started writing to temp file.
 Progress: =======================================================>100% |
 Finished writing to temp file.
ron@ubuntu:~$ 

---

### Post by Filthy Stockings on 2011-06-21
So sorry am late with replying...where does the time go?

Thanks, yet again for helpful info and following your new directions got the result!

Can now remove big fat pictures of DJs etc and allow freaky animations to run; flashing lights and movement keep dumb animals distracted.

Hope you enjoy the SMILEYS; heard em on R4 first time around.

Presume RUBICON is trying to do the same for the CIA.......

Good luck with all you do!

SA

---

### Post by Filthy Stockings on 2011-06-28
2050 28 6 11

Hello anyone out there.........

Cannot find **THE RADIO BALLADS; **
**[SIZE=3]Ballad of the Miners' Strike [/SIZE]**

**[SIZE=3][SIZE=1]which was on RADIO 2 21 6 11 and due to expire from IPLAYER around midnight tonight.[/SIZE][/SIZE]**


Did usual get-iplayer --type=radio and got a page of programmes BUT cannot find the above; have searched via THE RADIO/BALLAD OF/MINERS/RADIO/THE BALLAD etc and then tried the earlier PID type search, [found what I think, in my novice technical way, is the right PID [I][B]
b00r336f
[/B][/I]via starting the IPLAYER stream at source and right clicking....this the right way?] which have never had to use before BUT to no avail; just got this

[I]get-iplayer --get --type=radio --pid=**b00r336f**
get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

WARNING: Please download and run latest installer or install the XML::Simple perl module to use the Series and Brand pid parsing functionality
INFO: Trying pid: b00r336f using type: radio
INFO Trying to stream pid using type radio
INFO: pid not found in radio cache
ERROR: Failed to get version pid metadata from iplayer site

[/I]would prefer NOT to have to download more software as the one been using for few weeks seems exactly suited to my needs.

Could this be a consession to BBC by some ubuntu friendly employee; ie removing reference to the programme.

Have been told previously that 4oD have asked not to be 'GOT' and the community has obliged.

With the range of EVERYTHING ELSE being available, though, seems odd that just this one programme is not being offered.

ALSO anyone used a system to capture the BBC IPLAYER ARCHIVED stuff ie old START THE WEEKS/IN OUR TIME etc which used to be available via BBC site to stream.....FOREVER?

Get iplayer just lists the latest 7 DAY running titles and NOT previous stuff, even though it is gladly streamed by BBC via its own site.....without a cut-off period.

Any advice/help/comments most welcome.

Thanks in advance

SA

---

### Post by nothingspecial on 2011-06-28
Just got your post with an hour and a half to go.

I got it just like this


```
get_iplayer --type=radio --pid=b00r33b2
```

Maybe you got the incorrect pid

hope you get this in time.

---

### Post by Filthy Stockings on 2011-07-01
Hello

Thanks for reply and advice; sorry late getting back [0845 1 7 11]....why does life interfere with LOGGING IN?

Despite fearing I was too late to catch the stream, with your CORRECT pid, I gave it a shot just now AND IT WORKED!

Very odd as cannot even see the programme listed in the RADIO BALLADS site

[http://www.bbc.co.uk/radio2/radioballads/2006/steel/steel_songs.shtml](http://www.bbc.co.uk/radio2/radioballads/2006/steel/steel_songs.shtml)

but plays fine.

AND tried the same process at the IN OUR TIME site,

[http://www.bbc.co.uk/radio4/features/in-our-time/](http://www.bbc.co.uk/radio4/features/in-our-time/)

and your method WORKS to capture all the archived programmes, so DOUBLE THANKS!

ONE OTHER TECH QUERY; Tried to access the clips from the RADIO BALLADS site, as only clips seem on offer and found the option to SAVE appears, so took that but all this gives me is

RealMedia Metafile (application/ram)

which does not seem to play.

Is there an UBUNTU method to capture the clips and hear them?

Seems like there IS a SAVE option so curious why neither MEDIA PLAYER, nor BANSHEE seem to recognise the files then selected and do not play them.

Thanks very much and good luck with your day.

SA

---

### Post by Filthy Stockings on 2011-07-01
ooops 

in above

for MEDIA PLAYER I really mean MOVIE PLAYER.............

presume that is what plays the subsequently GOTiplayer programmes....or would it be Banshee?

Any road.........didn't want to further confuse my already confused querying.

SA

---

### Post by Filthy Stockings on 2011-07-14
THU 14 7 11
Can't see how to post a NEW QUESTION on FORUM H/PAGE NEW POSTS  pages so am trying here.

Anyone else having problems with GET-IPLAYER today?

Keep getting truncated programmes eg

TITUS GROAN/RUSSIA WILD EAST/THE MEDIA SHOW;C PATTEN/SOFT POWER HARD NEWS...all seemed to DL normally but then found the files only 1.8MB or thereabouts meaning some only lasted 1 minute or 13minutes of a scheduled hour programme such as TITUS GROAN;TITUS ARRIVES.

Hopefully just a blip but after a month of using the system without problem am concerned if this spells the end of the facility.

Anyone who can offer advice re this AND/OR where it is you post a new item....such as this topic which has only arisen today.

Thanks 

SA

---

### Post by majedaly on 2011-11-09
I use audacity, straight forward. and great

---

