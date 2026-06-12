---
title: "LIRC fine tuning with mplayer OSD"
date: 2008-02-01
forum: Mythbuntu
---

### Post by sikk on 2008-02-01
Hello,

Recently my wife asked me if it was possible to reduce the effort of turning on the mplayer OSD to see how much time was left in a file. My current setup was to use lirc to send a single mlpayer "osd" command per the mapped button. After some reading I discovered the you could send multiple mplayer commands by seperating commands with a "\n".

So. I have modified my .lircrc file to include mappings to  "OSD Toggle" by sending two OSD commnads to mplayer.

My lirc configuration for my toggle button looks like this.


```
# Show elapsed and total time OSD
begin
       remote = mceusb
       prog = mplayer
       button = More
       config = osd\nosd
       repeat = 0
       delay = 0
end
```

The result is that one button press shows elapsed and total times. One more press resets mplayers OSD state to enabled. Neat.

I decided to take this one step further and setup Pause to automatically turn on the OSD to show elapsed and total times when pause was used, then turn it off when playback was resumed.

To do this, some more reading on lirc was needed, becasue a simple "config = osd\nosd\npause" did not turn off the osd when playback was resumed. That is until I found that adding multiple config lines to lirc allowed the same button press to have different functions. 

Here is the extract from my lirc config file.

```
# Show elapsed and total time OSD on pause. Turn off on playback.
begin
       remote = mceusb
       prog = mplayer
       button = Pause
       config = osd\nosd\npause
       config = pasue\nosd\nosd
       repeat = 0
       delay = 0
end
```

The second config line is used each alternate "Pause" press. Theortically you could add more.

This is not a problem for me, and so does not require a response. But I was so impressed with the added function as well as the potential for other "macro" style mplayer applications that I felt I should share. 

Especially since I could not find a direct post that collerated the use of these two fuctions, either here or on the myth mailing list.

Feel free to share other combos that fine tune mplayer......

Sikko.

---

### Post by auburn on 2010-10-24
I've been working with your code snipet for more than a year now and as I find myself fine tuning it today I discovered I hadn't thanked you for it. Thank you, this is really cool!

---

