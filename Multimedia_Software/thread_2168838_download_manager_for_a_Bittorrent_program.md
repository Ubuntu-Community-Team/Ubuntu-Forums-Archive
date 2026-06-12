---
title: "download manager for a Bittorrent program?"
date: 2013-08-19
forum: Multimedia Software
---

### Post by nicholas4 on 2013-08-19
Hi i cant seem to find a program that will let me set my torrent program (qBittorrent) to start at a certain time and end at a certain time i have hughes net so downloading eats up my enternet time unless i do it durning there free download times which is from 2am to 6am and i already have a program that shuts my computer off at 6am but i dont want to have to stay up til 2 am every night to start my downloads does anyone know of a program that can help me with this that works with a torrent program? or that is a torrent program its self?

---

### Post by ian-weisser on 2013-08-19
Transmission torrent client, included with the default install of Ubuntu, has schedule settings for network usage to address precisely the problem you describe.

If you really want to get slightly more complicated, setting up a 'cron' job or 'at' job to launch/kill any application (including a torrent application), or to connect/disconnect from the network, or to shutdown the system, is not difficult at all.

---

### Post by nicholas4 on 2013-08-19
I tried using Transmission but for some reason ubuntu doesnt pull it up when i download a torrent like its not on the launch application screen thats why i downloaded qBittorrent because there is a seach function in the program its self im very new to ubuntu and really dont know exactly what im doing im kinda guessing so i may be doing something wrong im not the best with computers

---

### Post by ian-weisser on 2013-08-19
Your writing style is difficult to understand.

It seems like you are asking how to associate torrent files with Transmission (or any application).

The easy way is to associate helper applications for different filetypes (like .torrent) in your web browser.
Look for the "Applications" setting in your browser. It's very easy.

---

### Post by shantiq on 2013-08-19
[FONT=arial]hi nicholas


you can use [cron]("http://www.scrounge.org/linux/cron.html") for this    [more info]("https://help.ubuntu.com/community/CronHowto")

1. create file in home folder where to store your instructions

```
sudo gedit TIMES.cron

```

2. copy and paste and save instructions [start qbittorrent at 2.00 am every day in this case]

[/FONT]```
0 2 * * * env DISPLAY=:0 qbittorrent[FONT=arial]
[/FONT]
```[FONT=arial]
3.  in terminal [/FONT][FONT=arial] to record this [/FONT][FONT=arial]enter    ```
crontab TIMES.cron
```

4. [/FONT][FONT=arial] to see all ok [/FONT][FONT=arial]run   ```
crontab-l 
```
[/FONT]


crontab-r     to cancel



[SIZE=2][B]if you do not have to use
[/B]

kbittorrent but can use ktorrent instead it has a scheduler plugin   which you find by going to view/plugins and activate then set your times and limits
[/SIZE]


[ATTACH=CONFIG]245485[/ATTACH][ATTACH=CONFIG]245486[/ATTACH]

---

### Post by nicholas4 on 2013-08-19
Im not the best with grammer lol im sorry about that. what im trying to say is that when i go to the a web site to download a torrent a widow pops up that says i need to launch an application but it doesnt list any applications for me to choose from only files and if i click on a file it does nothing either. Like i said this is the first time ive had ubuntu or any version of linux for that matter ive always used windows so im sorry if this easy and im just missing something

---

### Post by nicholas4 on 2013-08-19
[**[COLOR=#000000]shantiq[/COLOR]**]("http://ubuntuforums.org/member.php?u=870500")
Thanks im gonna try using ktorrent like you said the code thing confuses me a lot mostly because i dont want to mess up anything i need to watch some youtube videos i learn better by watching but thank you very much im gonna try that right now

---

### Post by shantiq on 2013-08-19
hi again


do what you are happy with :KS


ktorrent is really excellent anyway   .... best luck with it


the cron thing is easy too as i have written it all out for you and tested it so i know it is good but if you are not a code guy it may be a bit scary:KS

---

### Post by nicholas4 on 2013-08-19
ok so i downloaded ktorrent it it looks like it has a search function but how do i install what its asking because i saved the file but if i click on it nothing happens i love how ubuntu looks but it makes me feel dumb lol

---

### Post by nicholas4 on 2013-08-19
[ 						 							 ]("http://ubuntuforums.org/member.php?u=870500")[**[COLOR=#000000]shantiq[/COLOR]**]("http://ubuntuforums.org/member.php?u=870500")

ok so i decided to try the cron because i found a scheduled task application in the software center thats made to work with cron and it lets me preview it and cron worked! lol thank  you very much youve helped me tons if i could hand you a beer thru the internet i would lol.

i have one more question tho
can i use cron to shutdown my computer at 6am too and if so could you walk me thru on how to do that as well
thanks in advance

---

### Post by shantiq on 2013-08-20
ha ok    good question   yes sure it can do that too

but way better to use this amazing gui   called qshutdown    > sudo apt-get install qshutdown


i use it everyday as it is so simple to use   can use for hibernate too [on 13.04 hibernate needs to be [enabled]("http://www.itworld.com/operating-systems/354001/turn-hibernate-option-ubuntu-1304")]

[ATTACH=CONFIG]245500[/ATTACH]

---

