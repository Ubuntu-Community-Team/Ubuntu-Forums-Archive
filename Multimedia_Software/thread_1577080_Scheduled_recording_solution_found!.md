---
title: "Scheduled recording solution found!"
date: 2010-09-18
forum: Multimedia Software
---

### Post by rmcellig on 2010-09-18
After weeks of posting to this and other forums regarding a problem I had which needed to be resolved, I am happy to report that I found a solution that is pretty simple.

1. I installed Scheduled Tasks (the GUI for Cron)
2. I used this code in my setup arecord -t wav -f cd -d 120 /home/user/soundfile.wav which works great!

The one question I have is that I always have to go into the sound preferences to make sure the input is set to analog in. Is there a way around this so that I don't always have to do this? Maybe there is something I can put in the code above or maybe there is an easier way of doing this so that I can just set it and forget it or have it hard coded in the code if that makes any sense :)

This was the only thing that I needed to resolve if I were to switch to Linux full time. Now that I finally found an answer I can work with (unless someone has an even easier solution), I think I can comfortable call Linux my main OS along with my Mac :)

---

