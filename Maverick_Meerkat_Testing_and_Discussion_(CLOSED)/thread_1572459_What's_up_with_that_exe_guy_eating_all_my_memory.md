---
title: "What's up with that exe guy eating all my memory?"
date: 2010-09-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-09-11
How can I find out, who's responsible for making poor exe guy eat over 1.4 GiB of RAM? Once my swap gets touched, the system becomes awfully slow. :(

**Edit:**

Case solved, Chromium it is. Browsing Google Maps (satellite view) quickly hogs all my RAM.

---

### Post by feardotcom on 2010-09-11
Sounds like i will be sticking with my firefox

But dont feel bad, Pandora.com crashes after 15-30 mins of listening.

---

### Post by ronacc on 2010-09-11
not seeing that here on 64bit , tried on 2 different installs with both chromium and chrome scrolled around in map>satellite view and zoomed in and out , nothing abnormal ,

---

### Post by ktp on 2010-09-11
I am not seeing it also

---

### Post by MacUntu on 2010-09-11
Are you guys using nvidia-current by any chance? As this exe process had something like "--type=gpu-process" in its command, I assumed it's just the BLOB giving me troubles once again.

I cannot reproduce it with my notebook using Nouveau - will later try that driver with the affected machine. Maybe something to report if reproducible.

Not happy with the BLOB in Maverick.

PS: I'm using the Chromium daily PPA.

---

### Post by ktp on 2010-09-11
have you tried looking at:
> about:memory
in chromium to see what it says.  the gpu-process (GPU Acceleration) is new in Chromium 7 so it might have some bugs.

---

### Post by MacUntu on 2010-09-11
Nothing useful in there.

Probably GPU accel. isn't supported by Nouveau, thus not happening when using it. 

I'm wondering if my ooooold 6600 GT is even capable of doing such fancy stuff.

**Edit:**
Yep, no exe process with Nouveau.

---

### Post by ronacc on 2010-09-11
using nvidia-current here installed by system>admin>additional drivers ,see SS . what is this EXE ? I dont show that in system monitor or htop .

---

### Post by ronacc on 2010-09-11
oops checking with nvidia settings the nvidia driver for some reason was't active , re activated it rebooted and reran chromium , no change .

---

### Post by MacUntu on 2010-09-11
[[img]http://img.xrmb2.net/727944.jpg[/img]](http://img.xrmb2.net/images/925688.png)

Actually it's zooming in and out that starts the hogging.

Forgot that I'm currently using the new beta driver 260.19.04. Will later go through the trouble of manually removing it.

---

### Post by plun on 2010-09-11
Ok... I am running the 260 driver and Chromium daily...

Are you starting Chromium with this string ?

```
chromium-browser -enable-accelerated-compositing
```

Must test this but I cannot see any leakage with a short test....

---

### Post by MacUntu on 2010-09-11
Nope, simply with chromium-browser.

---

### Post by plun on 2010-09-11
> **MacUntu said:**
> Nope, simply with chromium-browser.

Ok... retesting...;)

Is it with Google Maps only ?

---

### Post by MacUntu on 2010-09-11
Just went back to 256.53 -> same thing. Starting with '-enable-accelerated-compositing' didn't change anything. Don't know any other pages where this could happen - my default browser is Opera. :)

---

### Post by plun on 2010-09-11
> **MacUntu said:**
> Just went back to 256.53 -> same thing. Starting with '-enable-accelerated-compositing' didn't change anything. Don't know any other pages where this could happen - my default browser is Opera. :)

Well... I cannot see any leakage with Chromium....

Firefox4 uses more memory.

I am running the 260 driver from X-swat and I also have Xorg-edgers enabled.

---

### Post by MacUntu on 2010-09-11
> **plun said:**
> Well... I cannot see any leakage with Chromium....

Firefox4 uses more memory.

I am running the 260 driver from X-swat and I also have Xorg-edgers enabled.

x86/x64? Do you see the exe process? What's your GPU? Maybe mine is just too old for this stuff.

---

### Post by ronacc on 2010-09-11
zooming in and out  moves my memory usage up and down by 20 MB . I'm using the 256.53 repo driver , I'll d/l the 290 and try that .

---

### Post by plun on 2010-09-11
> **MacUntu said:**
> x86/x64? Do you see the exe process? What's your GPU? Maybe mine is just too old for this stuff.

OK again...

- 64 bits

- GeForce GT 330M

I cannot see any exe-process.... I have Conky running all the time with the top 5 "hungry" processes.

No leakage....

---

### Post by cariboo on 2010-09-11
I'm using the same driver as ronacc, on a 64-bit install, using chromium and google maps, zooming in and out, I get an extra 20Mb ram usage, even leaving it for ½ an hour fully zoomed in I don't see any changes in ram usage.

---

### Post by MacUntu on 2010-09-11
Cool, you're all on x64 - I'm not. Will do a x64 install tomorrow unless someone here can confirm what I'm seeing. :)

Thanks guys for your feedback! :)

---

### Post by mc4man on 2010-09-11
> unless someone here can confirm what I'm seeing.

Happen to be on a older P4 - 32 bit, pretty simple to recreate, zooming in and out keeps taking more and more ram, closing google maps returns it.
screen shows - quit after hitting 678, started at 252

The exe here is /proc/self/exe

---

### Post by MacUntu on 2010-09-11
> **mc4man said:**
> Happen to be on a older P4 - 32 bit, pretty simple to recreate, zooming in and out keeps taking more and more ram, closing google maps returns it.
screen shows - quit after hitting 678, started at 252

The exe here is /proc/self/exe

Woohoo, thanks a bunch! ):P

Now, where to report? Hmmm... nvidia-graphics-drivers? Chromium upstream?

---

### Post by mc4man on 2010-09-11
Here's an log showing steady increase - read @4 sec. 30 times
```
doug@doug-desktop1:~$ pidstat  -r -p 2345 4 30
Linux 2.6.35-20-generic (doug-desktop1) 	09/11/2010 	_i686_	(2 CPU)

06:47:15 PM       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
06:47:19 PM      2345   2284.25      0.00  207952 112124  10.94  exe
06:47:23 PM      2345   3993.25      0.00  236088 135004  13.17  exe
06:47:27 PM      2345      0.00      0.00  236088 135004  13.17  exe
06:47:31 PM      2345   2232.50      0.00  252856 150304  14.67  exe
06:47:35 PM      2345   1987.00      0.00  265656 161652  15.77  exe
06:47:39 PM      2345   2303.75      0.00  272056 175608  17.14  exe
06:47:43 PM      2345      0.00      0.00  272056 175608  17.14  exe
06:47:47 PM      2345      0.00      0.00  272056 175608  17.14  exe
06:47:51 PM      2345   5825.75      0.00  306592 209812  20.47  exe
06:47:55 PM      2345   2027.75      0.00  325792 224888  21.94  exe
06:47:59 PM      2345   3972.25      0.00  347528 247536  24.15  exe
06:48:03 PM      2345   1986.50      0.00  360328 258876  25.26  exe
06:48:07 PM      2345   2284.75      0.00  373128 272688  26.61  exe
06:48:11 PM      2345   2338.50      0.00  379528 286876  27.99  exe
06:48:15 PM      2345   5237.25      0.00  410200 313408  30.58  exe
06:48:19 PM      2345      0.00      0.00  410200 313408  30.58  exe
06:48:23 PM      2345   4007.25      0.00  428120 341020  33.28  exe
06:48:27 PM      2345   4673.00      0.00  460476 363048  35.43  exe
06:48:31 PM      2345   2160.50      0.00  473276 375784  36.67  exe
06:48:35 PM      2345   1984.00      0.00  486076 387092  37.77  exe
06:48:39 PM      2345      0.00      0.00  486076 387092  37.77  exe
06:48:43 PM      2345      0.00      0.00  486076 387092  37.77  exe

06:48:43 PM       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
06:48:47 PM      2345      0.00      0.00  486076 387092  37.77  exe
06:48:51 PM      2345   1997.75      0.00  498876 398504  38.88  exe
06:48:55 PM      2345   4767.00      0.00  527012 427508  41.72  exe
06:48:59 PM      2345   1983.50      0.00  539812 438808  42.82  exe
06:49:03 PM      2345      0.00      0.00  539812 438808  42.82  exe
06:49:07 PM      2345   2783.50      0.00  559012 456384  44.53  exe
06:49:11 PM      2345      0.00      0.00  559012 456384  44.53  exe
06:49:15 PM      2345      0.00      0.00  559012 456384  44.53  exe
Average:         2345   2027.67      0.00  400561 301647  29.43  exe

```
You might want to try the repo version and see - if so file a bug against, otherwise the daily ppa

---

### Post by ronacc on 2010-09-11
installed the 290 driver , exactly the same as the 256 except slightly faster , mem use the same still no EXE .

---

### Post by MacUntu on 2010-09-11
> **mc4man said:**
> You might want to try the repo version and see - if so file a bug against, otherwise the daily ppa
Maverick's Chromium works fine, no exe at all. Will try to compile if from trunk tomorrow and report it upstream.

---

### Post by ktp on 2010-09-11
> **MacUntu said:**
> Woohoo, thanks a bunch! ):P

Now, where to report? Hmmm... nvidia-graphics-drivers? Chromium upstream?

i would report it to [crbug.com]("http://crbug.com")

---

### Post by ktp on 2010-09-11
> **MacUntu said:**
> Maverick's Chromium works fine, no exe at all. Will try to compile if from trunk tomorrow and report it upstream.

oh ya there is something going on with GPU process:

I just reproduced it using 64-bit chromium daily builds  (from ppa).  I enabled GPU acceleration by adding following to /etc/chromium-browser/default
> CHROMIUM_FLAGS="--enable-accelerated-compositing --enable-webgl"

If you goto [this website]("http://webkit.org/blog-files/3d-transforms/poster-circle.html"), which should show a 3d cylinder, and keep refreshing the page, GPU process will keep increasing memory.  But if I close the tab (I was in incognito mode), the memory goes back to normal.  

I am seeing the total browser memory increase (not the gpu process memory), when using google map, depending on if new images needs to be loaded. This memory doesn't get released when
I close the tab.

Let me know if you write up a bug...so I can star it.

**Edit:**
I don't think I am seeing google maps memory leaks issue...for me it seem to be image caches which increases the memory.  I was using chromium task manager (shift+escape) to look at private memory for the browser.  It seem to not increase if I zoom in or out, on the same location, i.e. no new images are loaded.

---

### Post by MacUntu on 2010-09-12
Sorry, you're not seeing what I see - if I zoom around in Google Maps, the exe process (not chromium-browser) quickly takes all available memory and then starts swapping around.

As for compiling trunk - haha, that's kind of a PITA (resource-wise). Guess I'll just wait for the next PPA update and then report it upstream.

---

