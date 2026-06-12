---
title: "Voulme Control Problem"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by gauravdott on 2008-04-02
I am using ubuntu 7.10 and my i am using HDA ATI SB (Alsa Mixer) for volume control. The problem is that when Line in is set till 47% or below it the sound is perfect but as soon as it goes beyond 47% it becomes crappy and starts decreasing . Can anyone tell me what's the  problem.

Thanks

Gaurav:)

---

### Post by erginemr on 2008-04-02
Can you please run **alsamixer** from the terminal and check that the dbGain value for the PCM volume level is not above zero? I have noticed in my system that when I increase PCM volume level higher than 74%, the sound starts to distort.

Please refer to:
[http://ubuntuforums.org/showpost.php?p=4492869&postcount=16](http://ubuntuforums.org/showpost.php?p=4492869&postcount=16)
[http://ubuntuforums.org/showpost.php?p=4108189&postcount=3](http://ubuntuforums.org/showpost.php?p=4108189&postcount=3)

---

