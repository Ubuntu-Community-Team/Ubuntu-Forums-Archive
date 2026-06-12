---
title: "watching BBC replays of Sochi Games with Ubuntu"
date: 2014-02-10
forum: Multimedia Software
---

### Post by shantiq on 2014-02-10
FIRST RUN:

```
get-iplayer Winter Olympics
```


you will find this kind of results

```
Added: 1235:    Winter Olympics - Sochi 2014: Day 2, Part 1 - 6.00am to 9.00am, BBC Sport, Sport,TV,Winter Olympics,Winter Sports, defaultAdded: 1236:    Winter Olympics - Sochi 2014: Day 2, Part 2, BBC Sport, Sport,TV,Winter Olympics,Winter Sports, default
Added: 1237:    Winter Olympics - Sochi 2014: Day 2, Part 3, BBC Sport, Sport,TV,Winter Olympics,Winter Sports, default
Added: 1238:    Winter Olympics - Today at the Games: Sochi 2014: Day 2, BBC Two, Highlights,Popular,Sport,TV,Winter Olympics,Winter Sports, default,
Added: 1241:    Winter Olympics - Sochi 2014 Highlights: 7. Day 2 Ski Jumping, BBC Sport, Ski Jumping,Sport,TV, default
Added: 1242:    Winter Olympics - Sochi 2014 Highlights: 4. Day 2 Men's Downhill, BBC Sport, Alpine Skiing,Sport,TV, default
Added: 1243:    Winter Olympics - Sochi 2014 Highlights: 5. Day 2 Women's Snowboard Slopestyle, BBC Sport, Snowboarding,Sport,TV, default
Added: 1245:    Winter Olympics - Sochi 2014 Highlights: 6. Day 2 Ice Hockey - Russia v Germany, BBC Sport, Ice Hockey,Sport,TV, default
Added: 1246:    Winter Olympics - Sochi 2014: Day 2, Part 1 - 9.00am to 11.00am, BBC Sport, Sport,TV,Winter Olympics,Winter Sports, default
Added: 1257:    World Business Report - 10/02/2014, BBC News, Factual,Money,News,TV, default,



```


Then pick the number you wish to see and run for example

```
get_iplayer --stream  -g 1242 --player="mplayer -cache 512 -"
```


this does not save the video to your computer it merely streams it like TV

you can replace mplayer with [mpv]("https://launchpad.net/~mc3man/+archive/mpv-tests")




if you are outside the UK and still wish to view BBC coverage you can more than likely do same using Tor as explained [here]("http://ubuntuforums.org/showthread.php?t=2199050&p=12910840#post12910840")
Tell us how you get on...

---

