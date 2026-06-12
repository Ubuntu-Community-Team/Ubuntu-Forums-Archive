---
title: "Theoretical Question about Frame Rates"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by dsierpin on 2006-02-02
Hello Forum,

After struggling with my video card and seeing all the impressive glxgears output, I began to wonder :-k .  Why do I need my video card to do 10,000 fps if my monitor only synchs 65 Hz?  I'd heard in a film class that movies are produced at a standard 24 fps, so I figured why do I need my video card to give me any more than that?  I looked it up in the [wikipedia]("http://en.wikipedia.org/wiki/Frame_rate"), and it says that few people can distinguish a flicker in images rendered above 75 Hz.

They do give an example of a 180 degree turn in 1 second resulting in images with 3 degree displacement, so I guess in this case a higher frame rate might be useful, but still, if my monitor can't do any better than those 65 Hz, why do I need a bleeding-edge video card?  Perhaps glxgears, not being a benchmark ;) , doesn't output the true frames per second.  In that case, what does it output?  And if fgl_glxgears is a more accurate measurement, the 300+ fps that people satisfied with their cards get with that tool still seems unnecessary.  Thanks in advance for any thoughts/info.

---

### Post by Lord Illidan on 2006-02-02
24 fps in a game does not cut it for me. As for Glxgears, that is hardly a good benchmark.. that explains the too high scores. We need something more serious to benchmark 3D performance on Linux. 10,000 fps is not realistic.

---

### Post by krusbjorn on 2006-02-02
I also wondered about how more than 24fps in a game would be desirable. Our brain can only register 24fps anyway, right? I'm no neuroscientist so this just boggles me.

---

### Post by Lord Illidan on 2006-02-02
At 24 fps, a game doesn't seem quite playable to me, imho. 35 onwards, yes. Otherwise it is too jerky.

Don't forget visuals are double buffered. I think what you read is 24 fps is actually 12 fps real life..

---

### Post by krusbjorn on 2006-02-02
But TV and movies are 24fps, arent they? Whats the difference between a movie and a shoot-em-up game?

I'm not questioning you, I'm just curious. :)

---

### Post by dsierpin on 2006-02-02
The wikipedia article says that the fps in video is interrupted by the shutter in projection devices, with the shutter frequency depending on the quality of the device.  So a 24fps film that is interrupted 3 times per frame gives a pulse frequency of 72 Hz, which is indistinguishable to the human eye.

Also:

> The first 3D first-person adventure game for a personal computer, 3D Monster Maze, had a framerate of approximately 6 fps, and was still a success, being playable and addictive.

While this game is probably not considered playable by today's standards, the example suggests that our current setups may be overkill.

---

### Post by DoorGunner on 2006-02-02
I have done a bit of experimenting around with this.

I think glxgears and fgl_glxgears are relatively good benchmarks I will explain why as i go.

I used an americas army empty server as my test area. My results ranged from 24fps up to 100fps. If i was still and looking at my fps i was getting around 24fps. when i was moving about it went up to 44 fps. Darker area movement was even greater at 60fps. It would occasionally spike up at over 100 fps. 

What is happening is if you are still you the screen isnt changing much, there is little need for the fps to increase. However, once you start moving or there is a lot of detail that is changing your fps will change. Remember that there is a fair bit of persistance in your monitor to adapt to low fps if there is little movement. Now when the screen is busy ie people moving around there is a need to have the fps increase to keep up with the movement.

This explains glxgears. There are 3 little wheels that are moving at mach 3. So you get really high fps to try and keep up with the graphic changes. It is a means of determining how much fps is possible out of your card. not how much is going to give you all the time. Remember the higher the fps the harder your chip is working. The harder your chip works the hotter it gets. So conservation of fps, when it is not needed, will keep the chip cooler and preserve its life. (like your cpu)

Try not to confuse fps and server lag (latency). It is internet lag that produces some of the problems with movement. The server is trying to keep up with the positions of X number of players spead out all over the world. Occasionally, the connection between your machine and the server will be delayed by these factors. This results in an syncing problem and lag is the result.

----------------------------------------------------------------------

although it is not quite the same mpg's work the similar way accept to save bandwidth and physical space. Mpg's try to capture movement and store those changes rather than complete frames in order to save hard drive space. As well, when transmitting a stream over the internet it only has to transmit the changes rather than a complete frame, thus saving bandwidth.

---

### Post by dsierpin on 2006-02-02
DoorGunner-

Thanks for your thoughts.  It makes sense that the diagnostics like glxgears are testing maximum possible performance rather than real-world performance.  I guess that's why glxgears isn't a good benchmarking tool, since a card with 10,000 fps in glxgears might not do any better in a game-playing scenario than a card that gets 1,000 fps.  To use your experiment as an example, they both might top out around 100 fps.

But the question remains:  why do we have video cards that render at much higher rates than we can perceive?  Much higher, in fact, than even our best monitors can synch to?  :-k

---

### Post by DoorGunner on 2006-02-02
Many games now have to handle denser graphics environments. It could be that the higher fps is just a spin off of the cards graphic handling ability. Remeber the days of the amiga 500 and its whopping 10 pixels per square inch......But who knows....lol

---

### Post by Alpha_toxic on 2006-02-02
I don't think that gfx cards can render that much fps. I mean they can if you play Quake 2, but try F.E.A.R. or sth and even the most advanced gfx cards will have trouble keeping up...
And except that, although the brain does pecieve everything over 24fps as a continual movement, at higher fps it does seem smoother. I've tried using multi-sampling on some videos and the diference IS noticable (not allways though).

---

