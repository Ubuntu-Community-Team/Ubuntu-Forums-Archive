---
title: "speaking alarm clock"
date: 2008-09-23
forum: Multimedia Software
---

### Post by skiwithpete on 2008-09-23
Hi,

I'm trying to find an alarm clock that will wake me up by reading today's weather forecast and maybe some headlines.

But I ain't got a clue how to do it, and I'm almost a complete newb. 

I found this alarm clock, 
[http://www.getdeb.net/app/Alarm+Clock](http://www.getdeb.net/app/Alarm+Clock)
but its obviously just the first step.

Is there a programme out there that already does this?
If not is there a voice reader?
If there is a voice reader is there a way to compile custom information for it to read?

Hope someone can help,
P

---

### Post by andrewc6l on 2008-09-23
One way would be by creating a cron job (man cron) to run a script that downloaded the weather (using wget or something like that) and passed it through festival (Linux text-to-speech).

You might start by figuring out how to use wget to get the text of a weather report, and put that in a script. Then install festival and see if you can make it say what you want. Once you're sure that's working, adding it to cron is pretty easy.

---

### Post by skiwithpete on 2008-09-24
I will look into that, but as I'm noob and we're open source... if anyone knows an answer or a part answer, I would love to hear it.

Will start with wget and will keep y'all posted.
[edit: There's lots of info here
[http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)
but I need to know what it is I'm trying to find to put it to use]

Accuweather is next

Is there another place that might be a resource for this?

---

### Post by andrewc6l on 2008-09-24
If you're in the US, forecast.weather.gov might be a good place to look for text-only forecasts (as opposed to HTML forecasts). festival is the voice reader you're looking for.

---

### Post by skiwithpete on 2008-09-25
I'm in London UK.

I've sent an email to accuweather asking for access to their XML feeds.  I reckon accuweather is best too because it will do world weather through a couple of configurable clicks.

So my next steps are get accuweather, put info into a file then build a cron (whatever the hell that is :).

If anyone knows what the key to accuweather is, or if there's already a wget for it (there must be... look at Cairo Dock) - Please let me know.

P

---

### Post by aeiah on 2008-09-25
i dont know about accuweather, but check out bbc weather. they have a[ 3 day forcast in xml format ]("http://feeds.bbc.co.uk/weather/feeds/rss/5day/id/3282.xml")and also in a text only version for the blind. this is for my location ID which is of chesterfield for the text only bit:

[http://www.bbc.co.uk/cgi-bin/education/betsie/parser.pl/0005/feeds.bbc.co.uk/print/weather/5day.shtml?id=3282&print#results](http://www.bbc.co.uk/cgi-bin/education/betsie/parser.pl/0005/feeds.bbc.co.uk/print/weather/5day.shtml?id=3282&print#results)

i parse the xml one for my [conky script on my desktop]("http://ubuntuforums.org/showpost.php?p=5124213&postcount=2577"), although i parse too much info for it to be directly useful to you i guess.

but if you want accuweather and cairo dock uses it, then perhaps look at the source code for the dock

---

### Post by skiwithpete on 2008-09-25
> **aeiah said:**
> 
but if you want accuweather and cairo dock uses it, then perhaps look at the source code for the dock

I've never coded anything in my life before... heck, I don't even know what source code is going to look like.  So opening cairo dock is pie in the sky stuff for me right now.

I'll have a look at your script tho.

Cool.

---

### Post by skiwithpete on 2008-09-27
RSS link to weather.com

[http://rss.weather.com/weather/rss/local/UKXX0085?cm_ven=LWO&cm_cat=rss&par=LWO_rss](http://rss.weather.com/weather/rss/local/UKXX0085?cm_ven=LWO&cm_cat=rss&par=LWO_rss)

I just can't figure out how to switch from English to Metric...  Hope someone can help.

---

### Post by minivitale on 2009-03-07
this is something that I am _very_ interested in.  If you would like any specific help, i have some knowledge of scripting and would enjoy working on this project.  so where are you with this project?

---

### Post by minivitale on 2009-03-15
OK, so I started working on a python app to do what I want it to (and some of what you suggested) and here's what I've got so far

$ python runner.py
Hello (user), it is Sunday, March 15 07:25 pm.
The forecast for tonight is Cloudy skies. Low 47F. Winds SSE at 10 to 20 mph.
You have no events on your Google Calendar today.
GOOG is up 0.89 at 324.42 dollars a share.
MSFT is down 0.36 at 16.65 dollars a share.

where (user) is the current login name, the forecast comes from weather.com based on US Zip code, the Google Calendar integration works, and the stocks come from a list supplied by the user. (grabbed from Yahoo Stocks)  I have no interface for this project yet, but it is all read back to me by my computer through festival.

Still TODO:

[LIST]
[*]new email notification (most likely only Gmail)
[*]parse weather notifications (ie 47F -> 47 degrees Fahrenheit, SSE to South-South-East)
[*]Local Traffic Updates (possibly going to be overlooked as I can't find a site with national traffic information)
[*]News (other than stock info - maybe Google Reader integration, Google News)
[*]Music before and after the update to wake up the user.
[*]interface, easy cron job setup
[/LIST]

Note: As this is an app I am writing for myself, I am mainly focusing on what I care about most (mainly Google Apps integration).  Once I get a moderately stable version I'll let you guys know. you can submit any feature requests you want, but know I'm a high school student messing with this in my free time and will be rather picky about what I add (especially things I wont use).

---

### Post by minivitale on 2009-03-15
> **skiwithpete said:**
> RSS link to weather.com

[http://rss.weather.com/weather/rss/local/UKXX0085?cm_ven=LWO&cm_cat=rss&par=LWO_rss](http://rss.weather.com/weather/rss/local/UKXX0085?cm_ven=LWO&cm_cat=rss&par=LWO_rss)

I just can't figure out how to switch from English to Metric...  Hope someone can help.

Quick word of advice: write a short function that takes English measurements and spits out Metric.  Weather.com does not seem to support metric fully and as such the conversions need to happen on your end.  If you're using python, the 're' package is your friend.

---

### Post by skiwithpete on 2009-03-16
Am trying to find my old code, but I think you're already well past where I got to.

Some notes:
- I found the email I'd received from Accuweather (as I'd like it to be able to work for the world not just USA), though the people of Accuweather had several conditions, including displaying the logo and having a click to forecasts...  I guess there is no world, standard, free weather service...  at least not that I've found.
- I was using wget and festival as well, though never made a parsing script.


Features I'd like to request
1) Metric
2) London, UK included

Thanks dude, and stay in touch (have PMed you),
P

---

### Post by whiterabbit7500 on 2009-03-16
i'm going to be looking into this as well later tonight, seems like a really cool idea.

---

### Post by skiwithpete on 2009-03-17
> **whiterabbit7500 said:**
> i'm going to be looking into this as well later tonight, seems like a really cool idea.

Can I make a suggestion? if (IF) you're going to make separate versions, I think you should make an extensible version.

Start with a basic alarm clock, and then add "plugins" to it for the various commands, including weather, news, etc.  ...even a screen with custom information.

Also, have found a link and am going to try to learn python.  Advice welcome.

---

### Post by minivitale on 2009-03-17
python is my language of choice and as such pretty much anything i'll do will be in python (i've done the majority of my full application programming in Java, but i'm now trying to go python as i like it more) so i would reccommend strongly learning python, it is really powerful and succint as far as programming languages go.

I will look further into the "base app + plugin" idea.

Right now i haven't actually written the "alarm" part, i'm just getting all the things i will want read back to me WHEN it is run. I'm not exactly sure how I would do a base app and plugins, as i've not really done this level of interfaces before (most of my stuff is just for personal use only and as such I usually end up leaving it with command line only access) but I will try to figure out the best way to do that. I found a way to get London, UK weather on weather.com:

[http://www.weather.com/outlook/travel/businesstraveler/narrative/UKXX0085](http://www.weather.com/outlook/travel/businesstraveler/narrative/UKXX0085)

what i'm working on currently is taking in those strings and turning "45F" into 45 degrees fahrenheit OR xx degrees celcius. Once i get that, it should pretty easy to get UK weather and turn it into celcius by a few settings.

---

### Post by skiwithpete on 2009-03-18
In terms of the alarm (or setting it to run at particular times) I understood that cron was the way to go.

[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

Again, I know very little about this, and I may be stating the obvious, but thought I'd say it anyways.

Mini - I'd still love for you to send me the source at the moment, just so I could learn from it.  I learnt HTML from looking at page sources, so I reckon if I have a look at what you're doing in python it will help me to understand how it works.

Cheers,

P

---

### Post by skiwithpete on 2009-03-21
Minivitale,

I really wish you'd send me the current source so I could help you build this thing.  At the moment I'm just waiting for it...

Trying to learn Python in silly examples from the inet just isn't as useful as seeing what you've written.

Let me know,

P

---

### Post by An85Zk9tc8rfjV8i on 2009-04-26
> **skiwithpete said:**
> RSS link to weather.com
[http://rss.weather.com/weather/rss/local/UKXX0085?cm_ven=LWO&cm_cat=rss&par=LWO_rss](http://rss.weather.com/weather/rss/local/UKXX0085?cm_ven=LWO&cm_cat=rss&par=LWO_rss) 

[http://rss.weather.com/weather/rss/local/UKXX0085](http://rss.weather.com/weather/rss/local/UKXX0085)
is sufficient


> **minivitale said:**
> London, UK weather on weather.com:
[http://www.weather.com/outlook/travel/businesstraveler/narrative/UKXX0085](http://www.weather.com/outlook/travel/businesstraveler/narrative/UKXX0085)


find the feed closest to you:
[http://www.weather.com/weather/rss/subscription](http://www.weather.com/weather/rss/subscription)

---

### Post by bngweber@gmail.com on 2010-05-05
This is what I have managed to complete so far putting an alarm clock together. It plays mp3, Uses festival as a text to speech engine. It reads time correctly, and weather based off of weather station near you. It pulls weather info via weather-util from [http://weather.noaa.gov/](http://weather.noaa.gov/)   and then just choose your location for ID. Also Gradually increases volume. Uses two files alarm1 in home directory, and wakeup-volume in /usr/local/bin

code for Alarm #
#!/bin/bash

sleep 3

PLAYER=/usr/bin/mplayer
SONG="$HOME/alarms/alarm.mp3"
killall wakeup-volume
/usr/local/bin/wakeup-volume&
$PLAYER -loop 1  "$SONG"
sleep 5
echo "Good Morning, I hope you slept good and I hope you have a great day" | festival --tts

echo "The time is $HR $MIN" | festival --tts


# Used by Glenn Weber <bngweber@gmail.com>
# Created by Ernest N. Wilcox Jr. 
# I can be contacted at <ewilcox@bex.net>

# This script is released under the GPL v 2 as  is. 
# I accept no liability if you choose to use it. 
# If you choose to improve my script, and make 
# your changes public, you must do the following: 
# 1. include my comments. 
# 2. identify yourself, 
# 3. note your changes under these comments. 
# 4. provide contact information 

# Set up a variable to hold the current minute
# of the hour using the date command:
MIN=$(date +"%M")

# And another to hold the current Hour:
HR=$(date +"%l")

# Use a case statement to change the minute
# number to the equivalent word, but make the
# zero minute "o'clock". Handle all sixty minutes
# of the hour so this works correctly for any time.

case $MIN in
"00") MIN="o'clock";;
"01") MIN="Oh - one";;
"02") MIN="Oh - two";;
"03") MIN="Oh - three";;
"04") MIN="Oh - four";;
"05") MIN="Oh - five";;
"06") MIN="Oh - six";;
"07") MIN="Oh - seven";;
"08") MIN="Oh - eight";;
"09") MIN="Oh - nine";;
"10") MIN="ten";;
"11") MIN="eleven";;
"12") MIN="twelve";;
"13") MIN="thirteen";;
"14") MIN="fourteen";;
"15") MIN="fifteen";;
"16") MIN="sixteen";;
"17") MIN="seventeen";;
"18") MIN="eighteen";;
"19") MIN="nineteen";;
"20") MIN="twenty";;
"21") MIN="twenty one";;
"22") MIN="twenty two";;
"23") MIN="twenty three";;
"24") MIN="twenty four";;
"25") MIN="twenty five";;
"26") MIN="twenty six";;
"27") MIN="twenty seven";;
"28") MIN="twenty eight";;
"29") MIN="twenty nine";;
"30") MIN="thirty";;
"31") MIN="thirty one";;
"32") MIN="thirty two";;
"33") MIN="thirty three";;
"34") MIN="thirty four";;
"35") MIN="thirty five";;
"36") MIN="thirty six";;
"37") MIN="thirty seven";;
"38") MIN="thirty eight";;
"39") MIN="thirty nine";;
"40") MIN="forty";;
"41") MIN="forty one";;
"42") MIN="forty two";;
"43") MIN="forty three";;
"44") MIN="forty four";;
"45") MIN="forty five";;
"46") MIN="forty six";;
"47") MIN="forty seven";;
"48") MIN="forty eight";;
"49") MIN="forty nine";;
"50") MIN="fifty";;
"51") MIN="fifty one";;
"52") MIN="fifty two";;
"53") MIN="fifty three";;
"54") MIN="fifty four";;
"55") MIN="fifty five";;
"56") MIN="fifty six";;
"57") MIN="fifty seven";;
"58") MIN="fifty eight";;
"59") MIN="fifty nine";;
*) echo "error with minute $MIN" | festival --tts;;
esac

# Use another case statement to do the following:
# Use the echo command to assemble the output
# text for the current time statement, change the
# number for the current hour to the equivalent
# word, and pipe the result to festival.

case $HR in
" 1") echo $INTRO "one, $MIN" | festival --tts;;
" 2") echo $INTRO "two, $MIN" | festival --tts;;
" 3") echo $INTRO "three, $MIN" | festival --tts;;
" 4") echo $INTRO "four, $MIN" | festival --tts;;
" 5") echo $INTRO "five, $MIN" | festival --tts;;
" 6") echo $INTRO "six, $MIN" | festival --tts;;
" 7") echo $INTRO "seven, $MIN" | festival --tts;;
" 8") echo $INTRO "eight, $MIN" | festival --tts;;
" 9") echo $INTRO "nine, $MIN" | festival --tts;;
"10") echo $INTRO "ten, $MIN" | festival --tts;;
"11") echo $INTRO "eleven, $MIN" | festival --tts;;
"12") echo $INTRO "twelve, $MIN" | festival --tts;;
*) echo "error with hour $HR and minute $MIN" | festival --tts;;
esac


sleep 1

echo "The current temperature is " | festival --tts
weather-util -i KUZA | grep Temperature | cut -c16-19 |   festival --tts;
echo "degrees outside and" | festival --tts
weather-util -i KUZA | grep Sky | cut -c19-35 | festival --tts;
sleep 2
echo "why don't you enjoy some more music" | festival --tts
sleep 5

PLAYER=/usr/bin/mplayer
SONG="$HOME/alarms/alarm2.mp3"
killall wakeup-volume
/usr/local/bin/wakeup-volume&
$PLAYER -loop 1  "$SONG"

sleep 3

exit


code for wakeup-volume #

#!/bin/bash


for ((i = 35; i <= 100; i++)) do
/usr/bin/amixer sset Master playback $i%
sleep .5
done

---

### Post by freedomAboveAll on 2011-04-08
awesome.  Thank you for posting this script.  

In addition, Ubuntu has an Alarm Clock app (or two) in its software center that can trigger scripts (in case you do not want to fiddle wwith crontab to trigger this).

---

