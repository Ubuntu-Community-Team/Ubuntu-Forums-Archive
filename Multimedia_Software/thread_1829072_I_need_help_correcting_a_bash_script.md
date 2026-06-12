---
title: "I need help correcting a bash script"
date: 2011-08-20
forum: Multimedia Software
---

### Post by tzily on 2011-08-20
```

[LIST=1]
[*]             JK Says:                                                   
                              [URL="http://pyther.net/blog/index.php/2010/08/iheartradio-command-line-mplayer/#comment-109"]
[/URL]                                           Here is a one-liner bash function that will allow you to stream any iheartradio station by typing: 
 iheartradio 
 function iheartradio { mplayer -quiet $(wget -O &#8211; -q  &#8220;http://p2.$1.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live&#8221;  | sed -n &#8220;s|.*primary_location=\&#8221;\(rtmp://[^\"]*\)\&#8221;.*|\1|p&#8221;) -novideo  >& /dev/null; }
[/LIST]

```Hello, i hope i'm posting in the right section. For some reason i can't really understand scripting language. Could anyone please make this work for me?
I'll try to explain what i'm doing here.

There's this flash radio site, and i want to access it from the terminal through a simple command.
The rtmp:// stream changes every hour or something like that. This stream can always be found into this xml page [http://p2.wrzx-fm.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live]("http://p2.kiis-fm.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live")

```
<stream id="909" primary_location="rtmp://cp21575.live.edgefcs.net/live/Ind_IN_WRZX-FM_OR@s7701?auth=daEbvahaVbMbyczbEd2bCdRcIbtd9dQaScm-bot39e-4q-ML4V7_9opFFom4GBvmytAq&aifp=1234&CHANNELID=909&CPROG=_&MARKET=INDIANAPOLIS-IN&REQUESTOR=WRZX-FM&SERVER_NAME=p2.wrzx-fm.ccomrcdn.com&SITE_ID=2005&STATION_ID=WRZX-FM&MNM=2&TYPEOFPLAY=0" backup_location=""/>
```the command that plays fine the radio in the terminal is: mplayer "rtmp://url" -novideo
so if it updates, i have to open the xml page again and again and copy the rtmp link to play.

aparently this guy figured out this script that should grab the rtmp url and run it in mplayer through a single command, but i'm an idiot and have no knowledge why it's not working

what i do know is that i need to put  #!/bin/bash  line at the beginning of my script and that i need to make it executable in order to actually run it, but it's not working

here's my script:
(i have replaced his  $1  from the script line with  wrzx-fm  because that's the radio's name btw)

```
#!/bin/bash
function iheartradio { mplayer -quiet $(wget -O &#8211; -q &#8220;[http://p2.wrzx-fm.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live&#8221;]("http://p2.wrzx-fm.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live%E2%80%9D") | sed -n &#8220;s|.*primary_location=\&#8221;\(rtmp://[^\"]*\)\&#8221;.*|\1|p&#8221;) -novideo >& /dev/null; }
``````
tzily@PC:~/Desktop$ chmod u+x iheartradio.sh
tzily@PC:~/Desktop$ 
```ok, and now to run the thing: 

```
tzily@PC:~/Desktop$ iheartradio
iheartradio: command not found
tzily@PC:~/Desktop$ iheartradio.sh
iheartradio.sh: command not found
tzily@PC:~/Desktop$ ./iheartradio.sh
tzily@PC:~/Desktop$ /.iheartradio.sh
bash: /.iheartradio.sh: No such file or directory
tzily@PC:~/Desktop$ .iheartradio.sh
.iheartradio.sh: command not found
tzily@PC:~/Desktop$ '/home/tzily/Desktop/iheartradio.sh'
tzily@PC:~/Desktop$ sudo iheartradio.sh
[sudo] password for tzily: 
sudo: iheartradio.sh: command not found
tzily@PC:~/Desktop$ 

```I'm trying hard to run it, but i assume the script needs something...
this might look pathetic for some experienced fellows around here, but i'm new to this and if i don't get it right, i can't sleep tonight :( please someone correct and test this for me. Please...

---

### Post by sanderd17 on 2011-08-20
First, put your scripts in CODE tags, not QUOTE tags. It's a pita to change all the quotes to ascii chars.

Second, if you put it in a script, you don't need to create a function, it's one of of both that you have to do. If you do both, the script will only create a function and won't execute that function.

And now I'm trying to split it up in parts and see why it's not working.

EDIT

note to self: - signs also change
2nd note to self, the url is http://p2.$1.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live without the space before _live

**It works**

After changing those quotes, --signs and removing the space in the URL, it just works (and off course not using a function and a script together).

---

### Post by tzily on 2011-08-20
what signs ?
btw it seems the site auto added the space between listen and _live
is this the working script ?

```
#!/bin/bash
{ mplayer -quiet $(wget -O &#8211; -q  &#8220;http://p2.$1.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live&#8221; | sed -n &#8220;s|.*primary_location=\&#8221;\(rtmp://[^\"]*\)\&#8221;.*|\1|p&#8221;)  -novideo >& /dev/null; }
```

---

### Post by tzily on 2011-08-20
```
PC:~/Desktop$ ./iheartradio.sh
./iheartradio.sh: line 2: p&#8221;: command not found
./iheartradio.sh: line 2: .*primary_location=&#8221;(rtmp://[^"]*)&#8221;.*: No such file or directory
./iheartradio.sh: line 2: 1: command not found
sed: -e expression #1, char 1: unknown command: `&#65533;'
tzily@PC:~/Desktop$ 

```

---

### Post by sanderd17 on 2011-08-20
you need to change the italic quotes to normal quotes. If you type something a word processor, or in this site, they automatically change the quotes to make it look better.

So not these quotes : “quote”

but these:

```

"quote"

```

Apart from the quote, the minus-sign also changed into a bit longer minus (after the wget command, change it back to a normal minus) and you have found that space issue.

---

### Post by .... on 2011-08-20
> **sanderd17 said:**
> you need to change the italic quotes to normal quotes. If you type something a word processor, or in this site, they automatically change the quotes to make it look better.

So not these quotes : “quote”

but these:

```

"quote"

```

Apart from the quote, the minus-sign also changed into a bit longer minus (after the wget command, change it back to a normal minus) and you have found that space issue.
IIRC, there is no difference between directed quotation marks and straight ones (i.e it's the same ASCII char code). Copying and pasting between programs that display quotation marks in a more readable manner and those that don't shouldn't be an issue.
Note: that isn't the case with the backtick(`) and the apostrophe(').

---

### Post by sanderd17 on 2011-08-20
> **.... said:**
> IIRC, there is no difference between directed quotation marks and straight ones (i.e it's the same ASCII char code). Copying and pasting between programs that display quotation marks in a more readable manner and those that don't shouldn't be an issue.
Note: that isn't the case with the backtick(`) and the apostrophe(').

There is a difference in this case. If you check out the HTML code, you will see that some quotes are noted as &quot; and others as &# 8220; (without the space off course, but there is no bloody way to type it otherwise).

---

### Post by tzily on 2011-08-20
> **sanderd17 said:**
> you need to change the italic quotes to normal quotes. If you type something a word processor, or in this site, they automatically change the quotes to make it look better.

So not these quotes : &#8220;quote&#8221;

but these:

```

"quote"

```Apart from the quote, the minus-sign also changed into a bit longer minus (after the wget command, change it back to a normal minus) and you have found that space issue.


allright so the new script is

```
#!/bin/bash
{ mplayer -quiet $(wget -O - -q  &#8220;http://p2.$1.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live&#8221; | sed -n &#8220;s|.*primary_location=\&#8221;\(rtmp://[^\"]*\)\&#8221;.*|\1|p&#8221;)  -novideo >& /dev/null; }
```or

```
#!/bin/bash
{ mplayer -quiet $(wget -O - -q  &#8220;http://p2.wrzx-fm.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live&#8221; | sed -n &#8220;s|.*primary_location=\&#8221;\(rtmp://[^\"]*\)\&#8221;.*|\1|p&#8221;)  -novideo >& /dev/null; }
```and output still fails on both:

```
PC:~/Desktop$ bash
PC:~/Desktop$ ./iheartradio
./iheartradio: line 2: .*primary_location=&#8221;(rtmp://[^"]*)&#8221;.*: No such file or directory
./iheartradio: line 2: p&#8221;: command not found
./iheartradio: line 2: 1: command not found
sed: -e expression #1, char 1: unknown command: `&#65533;'
PC:~/Desktop$
```i'm too dumb for this, but i think the xml page linking to the rtmp url differs or something

does the radio actually play for you after running the script ? :O

---

### Post by sanderd17 on 2011-08-20
All those errors still say that you use wrong quotes. Please change the quotes by straight ones.

---

### Post by tzily on 2011-08-20
oh you meant these quotes " "

ok then

the colors in gedit actually changed after replacing all "
```
#!/bin/bash
{ mplayer -quiet $(wget -O - -q  "http://p2.wrzx-fm.ccomrcdn.com/player/player_dispatcher.html?section=radio&action=listen_live" | sed -n "s|.*primary_location=\"\(rtmp://[^\"]*\)\".*|\1|p")  -novideo >& /dev/null; }
```

output is null :(

```
PC:~/Desktop$ ./iheartradio.sh
tzily@PC:~/Desktop$ 

```

---

### Post by sanderd17 on 2011-08-20
mine starts playing with that script (although it takes a few seconds).

Do you have mplayer installed? Just execute

```

mplayer

```
to be sure.

---

### Post by tzily on 2011-08-20
of course... :( it's my default video player
maybe i'm not starting the script correct

---

### Post by sanderd17 on 2011-08-20
do a

```

ls -al 
cat iheartradio.sh
./iheartradio.sh

```

and give the output. Than I can check where the problem is.

---

### Post by tzily on 2011-08-20
i'm not sure what went wrong, but i have corrected the quotes again and this time it plays fine
thank you sir for all your trouble
you are very nice helping me with this
it will be awesome playing it on my non flash compatible old android phone
i hope you'll have a wonderful day

[IMG]http://www.marios-bar.com/images/Beer.jpg[/IMG]

---

### Post by sanderd17 on 2011-08-20
What phone do you have?

---

### Post by tzily on 2011-08-20
htc hero
it's on the way
just ordered a cheap used one

it has flash lite, but that's not compatible with a lot of stuff, so the terminal is an excellent choice rather than buying an expensive phone

anyway, this is very useful for my desktop also, great shortcuts for few radios without crappy flash pages opened in the browser
+ that i had to filter the iheartradio site through an american web proxy or google cache to actually listen to the radios because of the country ip restrictions

---

### Post by sanderd17 on 2011-08-20
> **tzily said:**
> htc hero
it's on the way
just ordered a cheap used one

it has flash lite, but that's not compatible with a lot of stuff, so the terminal is an excellent choice rather than buying an expensive phone

That one is more expensive than my tattoo :D

BTW, I don't even have flash lite because it's a custom ROM, and flash lite depends on the HTC sense framework (which I don't use because it makes my phone slower).

But I'm happy with my tattoo, after installing Cyanogen with good CPU overclocking and governors, it goes as fast as modern phones.

---

### Post by tzily on 2011-08-20
yes exactly that i was going to flash C7 or MIUI with gingerbread on this one :d
i also considered the tattoo. but the screen is way too small for my big fingers while typing :)

---

