---
title: "Mythweather displays a blank screen when viewing"
date: 2009-09-07
forum: Mythbuntu
---

### Post by williammanda on 2009-09-07
Mythweather use to work when I installed it a couple of months ago. Now I get the gui background and the mythweather icon but nothing else (see attachment). I can see the data is being downloaded to these files:

/home/william/.mythtv/MythWeather/NDFD-18_Hour

2009-09-07T18:50:02 2009-09-07T18:33:02
$VAR1 = {'2009-09-07T08:00:00-0400,2009-09-07T20:00:00-0400' => {'probability-of-precipitation_12 hour' => '30'},'2009-09-07T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg','temperature_hourly' => '77'},'2009-09-07T20:00:00-0400,2009-09-08T08:00:00-0400' => {'probability-of-precipitation_12 hour' => '14'},'2009-09-07T23:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nfew.jpg','temperature_hourly' => '71'},'2009-09-08T02:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nfew.jpg','temperature_hourly' => '68'},'2009-09-08T05:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg','temperature_hourly' => '66'},'2009-09-08T08:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra10.jpg','temperature_hourly' => '65'},'2009-09-08T08:00:00-0400,2009-09-08T20:00:00-0400' => {'probability-of-precipitation_12 hour' => '21'},'2009-09-08T11:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg','temperature_hourly' => '75'},'2009-09-08T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg','temperature_hourly' => '83'}};

/home/william/.mythtv/MythWeather/NDFD-6_day

2009-09-07T18:50:02 2009-09-07T18:33:02
$VAR1 = {'2009-09-08T08:00:00-0400,2009-09-08T20:00:00-0400' => {'temperature_maximum' => '86'},'2009-09-08T11:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-08T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-08T17:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-08T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg'},'2009-09-08T20:00:00-0400,2009-09-09T09:00:00-0400' => {'temperature_minimum' => '63'},'2009-09-08T23:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg'},'2009-09-09T02:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg'},'2009-09-09T05:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg'},'2009-09-09T08:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra10.jpg'},'2009-09-09T08:00:00-0400,2009-09-09T20:00:00-0400' => {'temperature_maximum' => '85'},'2009-09-09T11:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-09T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-09T17:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-09T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/hi_nshwrs20.jpg'},'2009-09-09T20:00:00-0400,2009-09-10T09:00:00-0400' => {'temperature_minimum' => '61'},'2009-09-10T02:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nra20.jpg'},'2009-09-10T08:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-10T08:00:00-0400,2009-09-10T20:00:00-0400' => {'temperature_maximum' => '85'},'2009-09-10T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra30.jpg'},'2009-09-10T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nra30.jpg'},'2009-09-10T20:00:00-0400,2009-09-11T09:00:00-0400' => {'temperature_minimum' => '63'},'2009-09-11T02:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nra20.jpg'},'2009-09-11T08:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-11T08:00:00-0400,2009-09-11T20:00:00-0400' => {'temperature_maximum' => '85'},'2009-09-11T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-11T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/ntsra20.jpg'},'2009-09-11T20:00:00-0400,2009-09-12T09:00:00-0400' => {'temperature_minimum' => '63'},'2009-09-12T02:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/ntsra20.jpg'},'2009-09-12T08:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra20.jpg'},'2009-09-12T08:00:00-0400,2009-09-12T20:00:00-0400' => {'temperature_maximum' => '83'},'2009-09-12T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra40.jpg'},'2009-09-12T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nra40.jpg'},'2009-09-12T20:00:00-0400,2009-09-13T09:00:00-0400' => {'temperature_minimum' => '65'},'2009-09-13T02:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nra30.jpg'},'2009-09-13T08:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra30.jpg'},'2009-09-13T08:00:00-0400,2009-09-13T20:00:00-0400' => {'temperature_maximum' => '82'},'2009-09-13T14:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/tsra40.jpg'},'2009-09-13T20:00:00-0400' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/ntsra40.jpg'}};

I installed VDPAU and I saw where some people were having an issue with mythweather but I thought it was resolved.
Thanks

---

### Post by williammanda on 2009-09-09
I forgot to post the mythfrontend log.

```
Starting mythfrontend.real..
2009-09-09 11:28:59.680 New DB connection, total: 2
2009-09-09 11:28:59.680 Connected to database 'mythconverg' at host: 192.168.1.100
2009-09-09 11:28:59.681 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-09-09 11:28:59.681 Enabled verbose msgs:  important general
2009-09-09 11:29:00.539 No theme dir: /home/william/.mythtv/themes/Mythbuntu-8.04-wide
2009-09-09 11:29:00.540 Primary screen 0.
2009-09-09 11:29:00.540 Using screen 0, 1366x768 at 0,0
2009-09-09 11:29:00.540 No theme dir: /home/william/.mythtv/themes/Mythbuntu-8.04-wide
2009-09-09 11:29:00.540 Switching to wide mode (Mythbuntu-8.04-wide)
2009-09-09 11:29:00.709 Using the Qt painter
2009-09-09 11:29:00.709 JoystickMenuClient Error: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2009-09-09 11:29:00.726 lirc init success using configuration file: /home/william/.mythtv/lircrc
2009-09-09 11:29:01.610 Specified base font 'medium' does not exist for font clock
2009-09-09 11:29:01.610 Specified base font 'medium' does not exist for font small
2009-09-09 11:29:01.610 Specified base font 'medium' does not exist for font medium
2009-09-09 11:29:01.610 Specified base font 'medium' does not exist for font large
2009-09-09 11:29:01.610 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-09-09 11:29:01.666 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-09-09 11:29:01.753 Registering Internal as a media playback plugin.
2009-09-09 11:29:02.049 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-09-09 11:29:02.217 Starting update of NWS-XML
2009-09-09 11:29:02.221 Starting update of NDFD-6_day
2009-09-09 11:29:02.224 Starting update of NDFD-18_Hour
2009-09-09 11:29:02.228 No theme dir: /home/william/.mythtv/themes/Mythbuntu-8.04-wide
2009-09-09 11:29:03.040 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/william/.mythtv/MythWeather/NWS-XML KCHA has exited
2009-09-09 11:29:03.041 wind_gust::
2009-09-09 11:29:03.041 nrecoverable error parsing script output 
2009-09-09 11:29:04.815 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/william/.mythtv/MythWeather/NDFD-18_Hour +35.02,-085.12 has exited
```

---

### Post by williammanda on 2009-09-09
Also I wanted to add that weather via mythweb works ok.

---

### Post by azmyth on 2009-09-09
I had the same issue as a result of current conditions. I applied this fix.

[http://ubuntuforums.org/showpost.php?p=7802955&postcount=13](http://ubuntuforums.org/showpost.php?p=7802955&postcount=13)

and thanks to whoever did the fix.

---

### Post by williammanda on 2009-09-09
I decided to try mythweather once again and doing so once I was presented with the blank screen I hit the right arrow key. Once I did that I got the screen data. I found out that using the right or left arrow once presented with the mythweather screen worked. This is not a fix but just an observation. Also I'm having the same issue on another computer that I recently install 9.04 and mythbuntu. Both systems are 64 bit.

---

### Post by williammanda on 2009-09-09
> **azmyth said:**
> I had the same issue as a result of current conditions. I applied this fix.

[http://ubuntuforums.org/showpost.php?p=7802955&postcount=13](http://ubuntuforums.org/showpost.php?p=7802955&postcount=13)

and thanks to whoever did the fix.

I saw this post and was not totally comfortable with how to pursue the correction or what the result would be. It seemed the correction was to reduce the font size and or eliminate other pictures so that the screen data could be properly seen. If the solution could be explained in better detail, I could be better informed as to the possible route I could use this information. Please explain your situation and the outcome of the solution.
Thanks

---

### Post by azmyth on 2009-09-09
The problem I had is that some of the current conditions came back blank thus giving the script an error thus giving Mythweather an error thus causing the blank screen. Once I replaced the pl script with the one in the thread it went away.

/usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/mythtv/.mythtv/MythWeather/NWS-XML KPHX

Just run from command line and it may give you errors if so that is what's causing the blank screen.

I didn't mess with the font just swapped out pl files.

---

### Post by williammanda on 2009-09-09
> **azmyth said:**
> The problem I had is that some of the current conditions came back blank thus giving the script an error thus giving Mythweather an error thus causing the blank screen. Once I replaced the pl script with the one in the thread it went away.

/usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/mythtv/.mythtv/MythWeather/NWS-XML KPHX

Just run from command line and it may give you errors if so that is what's causing the blank screen.

I didn't mess with the font just swapped out pl files.

I tried the script and got this output:

```
william@C2Q:~$ /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/mythtv/.mythtv/MythWeather/NWS-XML KPHX
Can't locate NWSLocation.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl line 8.
BEGIN failed--compilation aborted at /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl line 8.

```

I think one of the reasons for the error is the location. I'm not sure but I did this before from the previous posts info and got the same result. I could be wrong. Also I had a blank screen when mythweather was invoked so I'm not sure we have the same problem.

If this is a fix....I wonder if this has be posted to mythtv for a fix?
Thanks

---

### Post by azmyth on 2009-09-10
Yeah, that was the same issue I had. I fixed it by doing something to the perl path but then I still got errors when running the script. I swapped out the pl file with the one in the link and I didn't need to make any changes to the new pl file. I did have to set the current conditions screen in mythweb since it was still pulling off BBC when setting up through the frontend. I'm running trunk though.

---

### Post by williammanda on 2009-09-12
I swapped out the old nwsxml.pl file with the updated one and got the same problem, no current conditions screen.
Thanks

---

### Post by rickyble on 2009-09-29
I ran the command line from the above posting and got all my stuff like I am suppose to but the info center pulls up a blank page.  I tried the right arrow thing too but no joy.  Any suggestions?

---

