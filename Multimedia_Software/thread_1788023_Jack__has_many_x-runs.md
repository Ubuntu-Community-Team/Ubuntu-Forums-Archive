---
title: "Jack  has many x-runs"
date: 2011-06-22
forum: Multimedia Software
---

### Post by stephenstop on 2011-06-22
p, li { white-space: pre-wrap; } Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1540092
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]00:22:38.039 Server configuration saved to "/home/owner/.jackdrc".[/COLOR]
 [COLOR=#999999]00:22:38.041 Statistics reset.[/COLOR]
 [COLOR=#999999]00:22:39.244 Client activated.[/COLOR]
 [COLOR=#9999CC]00:22:39.248 JACK connection change.[/COLOR]
 [COLOR=#CC9966]00:22:39.273 JACK connection graph change.[/COLOR]
 [COLOR=#CC66CC]00:23:12.903 XRUN callback (1).[/COLOR]
 delay of 7166.000 usecs exceeds estimated spare time of 2838.000; restart ...






I dont know what this means i have like a million x-runs and i dont know how to fixthem ,

---

### Post by stephenstop on 2011-06-22
p, li { white-space: pre-wrap; } run of at least 0.858 msecs
 **** alsa_pcm: xrun of at least 0.835 msecs
 **** alsa_pcm: xrun of at least 0.804 msecs
 **** alsa_pcm: xrun of at least 0.839 msecs
 **** alsa_pcm: xrun of at least 0.805 msecs
 **** alsa_pcm: xrun of at least 0.809 msecs
 **** alsa_pcm: xrun of at least 0.830 msecs
 **** alsa_pcm: xrun of at least 0.808 msecs
 **** alsa_pcm: xrun of at least 0.852 msecs
 **** alsa_pcm: xrun of at least 0.871 msecs
 **** alsa_pcm: xrun of at least 0.866 msecs
 **** alsa_pcm: xrun of at least 0.811 msecs
 **** alsa_pcm: xrun of at least 0.830 msecs
 **** alsa_pcm: xrun of at least 0.795 msecs
 **** alsa_pcm: xrun of at least 0.827 msecs
 **** alsa_pcm: xrun of at least 0.836 msecs
 **** alsa_pcm: xrun of at least 0.853 msecs
 **** alsa_pcm: xrun of at least 0.884 msecs
 **** alsa_pcm: xrun of at least 0.835 msecs
 **** alsa_pcm: xrun of at least 0.893 msecs
 **** alsa_pcm: xrun of at least 0.837 msecs
 **** alsa_pcm: xrun of at least 0.887 msecs
 **** alsa_pcm: xrun of at least 0.892 msecs
 **** alsa_pcm: xrun of at least 0.862 msecs
 **** alsa_pcm: xrun of at least 0.943 msecs
 **** alsa_pcm: xrun of at least 0.848 msecs
 **** alsa_pcm: xrun of at least 0.860 msecs
 **** alsa_pcm: xrun of at least 0.842 msecs
 **** alsa_pcm: xrun of at least 0.861 msecs
 **** alsa_pcm: xrun of at least 0.850 msecs
 **** alsa_pcm: xrun of at least 0.819 msecs
 **** alsa_pcm: xrun of at least 0.819 msecs
 **** alsa_pcm: xrun of at least 0.822 msecs
 **** alsa_pcm: xrun of at least 0.756 msecs
 **** alsa_pcm: xrun of at least 0.822 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.821 msecs
 **** alsa_pcm: xrun of at least 0.818 msecs
 **** alsa_pcm: xrun of at least 0.768 msecs
 **** alsa_pcm: xrun of at least 0.768 msecs
 **** alsa_pcm: xrun of at least 0.775 msecs
 **** alsa_pcm: xrun of at least 0.751 msecs
 **** alsa_pcm: xrun of at least 0.879 msecs
 **** alsa_pcm: xrun of at least 0.805 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.765 msecs
 **** alsa_pcm: xrun of at least 0.816 msecs
 **** alsa_pcm: xrun of at least 0.811 msecs
 **** alsa_pcm: xrun of at least 0.807 msecs
 **** alsa_pcm: xrun of at least 0.762 msecs
 **** alsa_pcm: xrun of at least 0.800 msecs
 **** alsa_pcm: xrun of at least 0.846 msecs
 **** alsa_pcm: xrun of at least 0.880 msecs
 **** alsa_pcm: xrun of at least 0.850 msecs
 **** alsa_pcm: xrun of at least 0.889 msecs
 **** alsa_pcm: xrun of at least 0.782 msecs
 **** alsa_pcm: xrun of at least 0.892 msecs
 **** alsa_pcm: xrun of at least 0.802 msecs
 **** alsa_pcm: xrun of at least 0.819 msecs
 **** alsa_pcm: xrun of at least 0.766 msecs
 **** alsa_pcm: xrun of at least 0.804 msecs
 **** alsa_pcm: xrun of at least 0.841 msecs
 **** alsa_pcm: xrun of at least 0.829 msecs
 **** alsa_pcm: xrun of at least 0.773 msecs
 **** alsa_pcm: xrun of at least 0.817 msecs
 **** alsa_pcm: xrun of at least 0.849 msecs
 **** alsa_pcm: xrun of at least 0.811 msecs
 **** alsa_pcm: xrun of at least 0.838 msecs
 **** alsa_pcm: xrun of at least 0.777 msecs
 **** alsa_pcm: xrun of at least 0.797 msecs
 **** alsa_pcm: xrun of at least 0.816 msecs
 **** alsa_pcm: xrun of at least 0.812 msecs
 **** alsa_pcm: xrun of at least 0.834 msecs
 **** alsa_pcm: xrun of at least 0.794 msecs
 **** alsa_pcm: xrun of at least 0.818 msecs
 **** alsa_pcm: xrun of at least 0.840 msecs
 **** alsa_pcm: xrun of at least 0.825 msecs
 **** alsa_pcm: xrun of at least 0.836 msecs
 **** alsa_pcm: xrun of at least 0.813 msecs
 **** alsa_pcm: xrun of at least 0.834 msecs
 **** alsa_pcm: xrun of at least 0.875 msecs
 **** alsa_pcm: xrun of at least 0.801 msecs
 **** alsa_pcm: xrun of at least 0.876 msecs
 **** alsa_pcm: xrun of at least 0.818 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.894 msecs
 **** alsa_pcm: xrun of at least 0.822 msecs
 **** alsa_pcm: xrun of at least 0.871 msecs
 **** alsa_pcm: xrun of at least 0.815 msecs
 **** alsa_pcm: xrun of at least 0.810 msecs
 **** alsa_pcm: xrun of at least 0.859 msecs
 **** alsa_pcm: xrun of at least 0.789 msecs
 **** alsa_pcm: xrun of at least 0.838 msecs
 **** alsa_pcm: xrun of at least 0.803 msecs
 **** alsa_pcm: xrun of at least 0.831 msecs
 **** alsa_pcm: xrun of at least 0.895 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.803 msecs
 **** alsa_pcm: xrun of at least 0.847 msecs
 **** alsa_pcm: xrun of at least 0.766 msecs
 **** alsa_pcm: xrun of at least 0.787 msecs
 **** alsa_pcm: xrun of at least 0.770 msecs
 **** alsa_pcm: xrun of at least 0.826 msecs
 **** alsa_pcm: xrun of at least 0.852 msecs
 **** alsa_pcm: xrun of at least 0.845 msecs
 **** alsa_pcm: xrun of at least 0.839 msecs
 **** alsa_pcm: xrun of at least 0.803 msecs
 **** alsa_pcm: xrun of at least 0.823 msecs
 **** alsa_pcm: xrun of at least 0.788 msecs
 **** alsa_pcm: xrun of at least 0.828 msecs
 **** alsa_pcm: xrun of at least 0.851 msecs
 **** alsa_pcm: xrun of at least 0.835 msecs
 **** alsa_pcm: xrun of at least 0.822 msecs
 **** alsa_pcm: xrun of at least 0.876 msecs
 **** alsa_pcm: xrun of at least 0.753 msecs
 **** alsa_pcm: xrun of at least 0.792 msecs
 **** alsa_pcm: xrun of at least 0.818 msecs
 **** alsa_pcm: xrun of at least 0.766 msecs
 **** alsa_pcm: xrun of at least 0.869 msecs
 **** alsa_pcm: xrun of at least 0.746 msecs
 **** alsa_pcm: xrun of at least 0.826 msecs
 **** alsa_pcm: xrun of at least 0.812 msecs
 **** alsa_pcm: xrun of at least 0.767 msecs
 **** alsa_pcm: xrun of at least 0.863 msecs
 **** alsa_pcm: xrun of at least 0.776 msecs
 **** alsa_pcm: xrun of at least 0.808 msecs
 **** alsa_pcm: xrun of at least 0.819 msecs
 **** alsa_pcm: xrun of at least 0.772 msecs
 **** alsa_pcm: xrun of at least 0.783 msecs
 **** alsa_pcm: xrun of at least 0.818 msecs
 **** alsa_pcm: xrun of at least 0.860 msecs
 **** alsa_pcm: xrun of at least 0.877 msecs
 **** alsa_pcm: xrun of at least 0.861 msecs
 **** alsa_pcm: xrun of at least 0.850 msecs
 **** alsa_pcm: xrun of at least 0.787 msecs
 **** alsa_pcm: xrun of at least 0.809 msecs
 **** alsa_pcm: xrun of at least 0.870 msecs
 **** alsa_pcm: xrun of at least 0.788 msecs
 **** alsa_pcm: xrun of at least 0.784 msecs
 **** alsa_pcm: xrun of at least 0.770 msecs
 **** alsa_pcm: xrun of at least 0.826 msecs
 **** alsa_pcm: xrun of at least 0.830 msecs
 **** alsa_pcm: xrun of at least 0.798 msecs
 **** alsa_pcm: xrun of at least 0.785 msecs
 **** alsa_pcm: xrun of at least 0.777 msecs
 **** alsa_pcm: xrun of at least 0.796 msecs
 **** alsa_pcm: xrun of at least 0.820 msecs
 **** alsa_pcm: xrun of at least 0.804 msecs
 **** alsa_pcm: xrun of at least 0.828 msecs
 **** alsa_pcm: xrun of at least 0.850 msecs
 **** alsa_pcm: xrun of at least 0.828 msecs
 **** alsa_pcm: xrun of at least 0.849 msecs
 **** alsa_pcm: xrun of at least 0.824 msecs
 **** alsa_pcm: xrun of at least 0.809 msecs
 **** alsa_pcm: xrun of at least 0.828 msecs
 **** alsa_pcm: xrun of at least 0.858 msecs
 **** alsa_pcm: xrun of at least 0.853 msecs
 **** alsa_pcm: xrun of at least 0.765 msecs
 **** alsa_pcm: xrun of at least 0.876 msecs
 **** alsa_pcm: xrun of at least 0.810 msecs
 **** alsa_pcm: xrun of at least 0.774 msecs
 **** alsa_pcm: xrun of at least 0.824 msecs
 **** alsa_pcm: xrun of at least 0.788 msecs
 **** alsa_pcm: xrun of at least 0.804 msecs
 **** alsa_pcm: xrun of at least 0.877 msecs
 **** alsa_pcm: xrun of at least 0.826 msecs
 **** alsa_pcm: xrun of at least 0.819 msecs
 **** alsa_pcm: xrun of at least 0.777 msecs
 **** alsa_pcm: xrun of at least 0.789 msecs
 **** alsa_pcm: xrun of at least 0.792 msecs
 **** alsa_pcm: xrun of at least 0.777 msecs
 **** alsa_pcm: xrun of at least 0.761 msecs
 **** alsa_pcm: xrun of at least 0.828 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.865 msecs
 **** alsa_pcm: xrun of at least 0.803 msecs
 **** alsa_pcm: xrun of at least 0.864 msecs
 **** alsa_pcm: xrun of at least 0.852 msecs
 **** alsa_pcm: xrun of at least 0.870 msecs
 **** alsa_pcm: xrun of at least 0.866 msecs
 **** alsa_pcm: xrun of at least 0.801 msecs
 **** alsa_pcm: xrun of at least 0.826 msecs
 **** alsa_pcm: xrun of at least 0.812 msecs
 **** alsa_pcm: xrun of at least 0.807 msecs
 **** alsa_pcm: xrun of at least 0.922 msecs
 **** alsa_pcm: xrun of at least 0.783 msecs
 **** alsa_pcm: xrun of at least 0.843 msecs
 **** alsa_pcm: xrun of at least 0.833 msecs
 **** alsa_pcm: xrun of at least 0.745 msecs
 **** alsa_pcm: xrun of at least 0.763 msecs
 **** alsa_pcm: xrun of at least 0.764 msecs
 **** alsa_pcm: xrun of at least 0.818 msecs
 **** alsa_pcm: xrun of at least 0.830 msecs
 **** alsa_pcm: xrun of at least 0.852 msecs
 **** alsa_pcm: xrun of at least 0.815 msecs
 **** alsa_pcm: xrun of at least 0.784 msecs
 **** alsa_pcm: xrun of at least 0.789 msecs
 **** alsa_pcm: xrun of at least 0.808 msecs
 **** alsa_pcm: xrun of at least 0.810 msecs
 **** alsa_pcm: xrun of at least 0.836 msecs
 **** alsa_pcm: xrun of at least 0.799 msecs
 **** alsa_pcm: xrun of at least 0.763 msecs
 **** alsa_pcm: xrun of at least 0.788 msecs
 **** alsa_pcm: xrun of at least 0.804 msecs
 **** alsa_pcm: xrun of at least 0.862 msecs
 **** alsa_pcm: xrun of at least 0.780 msecs
 **** alsa_pcm: xrun of at least 0.839 msecs
 **** alsa_pcm: xrun of at least 0.755 msecs
 **** alsa_pcm: xrun of at least 0.785 msecs
 **** alsa_pcm: xrun of at least 0.851 msecs
 **** alsa_pcm: xrun of at least 0.780 msecs
 **** alsa_pcm: xrun of at least 0.757 msecs
 **** alsa_pcm: xrun of at least 0.843 msecs
 **** alsa_pcm: xrun of at least 0.807 msecs
 **** alsa_pcm: xrun of at least 0.820 msecs
 **** alsa_pcm: xrun of at least 0.776 msecs
 **** alsa_pcm: xrun of at least 0.780 msecs
 **** alsa_pcm: xrun of at least 0.855 msecs
 **** alsa_pcm: xrun of at least 0.750 msecs
 **** alsa_pcm: xrun of at least 0.813 msecs
 **** alsa_pcm: xrun of at least 0.796 msecs
 **** alsa_pcm: xrun of at least 0.819 msecs
 **** alsa_pcm: xrun of at least 0.843 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.787 msecs
 **** alsa_pcm: xrun of at least 0.810 msecs
 **** alsa_pcm: xrun of at least 0.849 msecs
 **** alsa_pcm: xrun of at least 0.875 msecs
 **** alsa_pcm: xrun of at least 0.814 msecs
 **** alsa_pcm: xrun of at least 0.742 msecs
 **** alsa_pcm: xrun of at least 0.847 msecs
 **** alsa_pcm: xrun of at least 0.808 msecs
 **** alsa_pcm: xrun of at least 0.782 msecs




this just happened when using ardour,i was trying to create sends for effects instead of like 3 effects on like 6 tracks and it froze up.....:(

---

### Post by kayosiii on 2011-06-22
are you running jack with realtime privileges?

---

### Post by stephenstop on 2011-06-22
yes i am

---

### Post by cchhrriiss121212 on 2011-06-22
You need to increase your frames setting, 128 would only work if you have good hardware and a low latency kernel installed.

---

### Post by stephenstop on 2011-06-22
Ok thanks but what should i increase it to?and is their anything else i need to/could do?

---

### Post by cchhrriiss121212 on 2011-06-23
The latency you can get depends on your hardware, so I can't tell you what to set it as. Integrated soundcards are not designed for low latency audio work, so just increase the frames until it is happy.

Also try disabling any CPU scaling (right click on the task bar and add the applet), and running jack in synchronous mode (just add "-S" to the server path in qjackctl).

---

### Post by stephenstop on 2011-06-23
Ok thanks I didnt think about that,thank you for taking the time to help me,i really need some friends!thanks dude.



/usr/bin/jackd is the server path and i added -S and it said it could not connect,under setup is that what you meant?

---

### Post by cchhrriiss121212 on 2011-06-24
Yes that is what I meant, but I think that option only works on jack2.

Do you have the realtime box checked in jack setup? It will run much better in realtime mode. Soft mode may also help cut down on xruns.

---

### Post by stephenstop on 2011-06-26
Ok thanks man yea i have that checked,they are less{the x-runs},how do i get jack 2 and what is its difference and is jack 2 better,i have not been able to understand how to change a program;say hydrodrums(h2).9.4 which i have into the .9.5version,could you help me figure it out?I havemany progrrams I want to update ,like zynsubfx into yoshimi.T

Thanks alot my friend,I never knew much about windows and this is my first linux computer

---

### Post by cchhrriiss121212 on 2011-06-26
jack2 is the same as jack1, but it has support for dual core CPUs, so it may work a little better for some people. If you have jack1 I would stick with it for the time being.

I explained about newer software in the thread you posted to in the studio forum, which should cover what you mention here.

---

