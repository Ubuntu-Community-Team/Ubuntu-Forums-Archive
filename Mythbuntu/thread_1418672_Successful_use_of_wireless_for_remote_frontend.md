---
title: "Successful use of wireless for remote frontend"
date: 2010-02-28
forum: Mythbuntu
---

### Post by svwhisper on 2010-02-28
I've seen a number of posts over time that indicate wireless networking is problematic.  I wanted to let others know there may be a workable solution after all.  I am quite happy with my configuration, which is using a Ruckus wireless 802.11N 5gHz access point and two of their client adapters.  My frontend Acer Revo is attached via ethernet to a Ruckus client adapter, which connects to the Ruckas AP sitting next to my Readynas NAS.  The backend (a high power homebuilt box) also connects via ethernet to a Ruckus client adapter and has livetv and recordings on local storage (i.e. not NAS).  Streaming HD livetv from the backend to the Revo is flawless, even when there is other high volume traffic from backend to NAS that drives the Ruckus client adapter to 50M bits/second (as reported by jnettop).

I am also able to simultaneously stream livetv HD content to a Thinkpad without causing any stuttering.  The Thinkpad uses its internal 802.11N adapter to connect with the Ruckus AP.

Note that I am not a techo or performance analyst-- just someone who wanted to share a workable approach to wireless for others not fortunate enough to have cat5 in every room.   Also, the AP is on the 3rd floor of a house, the Revo is on the 2nd floor and the backend lives on the ground floor.

Dave

---

### Post by williammanda on 2010-02-28
A couple questions concerning your setup:
1. What are the part numbers for your setup?
2. Have you had more than one wireless computer accessing data? If so report the outcome. I was looking at 2 to 3 wireless setups.
3. What was your signal quality? I used dd-wrt on my router and it gave the signal quality for the wireless computer. Ubuntu wireless software has a bug in reporting the correct signal quality.
4. What was the maximum distance from the AP to the wireless computer?
5. What drivers were used for the wireless network cards?

I tried a 2.4Ghz linksys wrt350n router using only N wireless but had good and bad days as far as the video / audio losing connection. Whether it was a neighbors wifi interference or just my signal quality. My router was 30' away from the computer and the signal was around 80. Also I ran a file transfer test. I copied 5GB file from a lan computer to the wireless computer. The transfer rate averaged 70 - 80 Mbs and spiked to 125 Mbs. I used the system monitor to watch the network transfer.

---

### Post by svwhisper on 2010-03-01
>A couple questions concerning your setup:
>1. What are the part numbers for your setup?

The Ruckus access point is a model 7811 and the client adapter is a 7111.  BTW, these are strange devices from a usability perspective.  They may make some sense to someone familiar with service provider gear, but they were completely foreign compared to the Dlink and Netgear kit I have used in the past.

>2. Have you had more than one wireless computer accessing data? If so report the >outcome. I was looking at 2 to 3 wireless setups.

As I mentioned above, I can watch HD livetv or recordings on the Acer Revo and a laptop simultaneously without stuttering.  Both are connected to the 7811 via 802.11N 5gHz.  With a single over the air live HD stream, jnettop on the backend reports a 9M bits/second TCP connection to the frontend via wireless.  I don't know if this is accurate or not, but seems about right.

>3. What was your signal quality? I used dd-wrt on my router and it gave the signal >quality for the wireless computer. Ubuntu wireless software has a bug in reporting the >correct signal quality.

Signal quality, as reported by the 7811 is 20dB for the backend (two floors away) and 29d dB for the Revo (one floor away).  Note that the Mythtv systems don't use wireless directly, but rather are connected by a 1 metre ethernet cable to the 7111 client adapters.

>4. What was the maximum distance from the AP to the wireless computer?

The signal from the 7811 must pass through two floors to hit the 7111, but the lateral distance is about 10 metres.

>5. What drivers were used for the wireless network cards?

There are no wireless drivers.  The 7111 client adapters connect to the Mythbuntu hosts via ethernet.  I'm really happy not to have to mess with wireless drivers.

Dave

---

### Post by williammanda on 2010-03-01
Here is something to go by when looking at signal data to determine your signal quality. This was taken from the dd-wrt site:

> Signal: (in dBm) A small negative number is good (-40 is good, -98 is bad)

Noise: (in dBm) A large negative number is good (-98 is good, -40 is terrible, -70 would be pretty bad in the real world)

SNR: (in dB) High is good (should be the same as difference between noise and signal, a difference of 20 would be great, a difference of 1 may barely work)
SNR(dB) = Signal(dBm) - Noise(dBm)

Signal Quality: High is good (somewhat like SNR but indexed to 100 with noise as the base, percentage of the best theoretical ideal quality in regards to your local-noise)

Signal - Noise = SNR
  -82  -  -98  = 16

Signal / Noise * SNR = Signal Quality
  -82  /  -98  * 16  = 13.4%

Typically, noise will be -92 which means you should get a clean connection with a signal as low as -92. However, expecting to hold a good connection with a signal lower than -85 (e.g. -90), is expecting too much. The signal can be improved by -3 dB by doubling the power setting at the transmitting radio, e.g., 100 mW increased to 200 mW would improve your signal from -85 to -82. Antennas with increased gain will also help. Say you had the standard 3 dB antenna and changed it for a 12 dB antenna, that's a 9 dB increase, so your signal would increase from -82 to -73 which would be an excellent signal, probably capable of 54 Mbps. Using the term excellent in terms of running a WISP, it would probably be only 3 bars on a 5 bar signal strength meter. Don't worry if, as a WISP your signal quality is low, like 14%. It's not really a problem since -82 is considered acceptable. 

I noticed you referred to db and I was referring to signal quality. I stated that I had a signal quality of 80 but that was the best. It ranged from 65 - 80. DB is only a part of the equation.

---

### Post by williammanda on 2010-03-01
After reading a few online write ups. It seems that this isn't traditional wireless. They have a unique approach which centralizes the transmission so that it cuts down on noise, etc... Not only that the connecting isn't standard wireless. It seems to do all of its work between the standard lan network connections. Where did you buy the devices? From Ruckus? I can't seem to find anyone that retails them. I'm very is interested in trying this out. Also could you trial more than 2 simultaneous transmissions? According to their site you can do 4 - 6 mpeg2 transmissions at the same time.

> For video applications using a Ruckus 7811, a Ruckus multimedia network is optimized to assure transmission of 40-60 Mbps at 99% guaranteed packet delivery throughout a typical home (2500ft2 / 230m2). This performance target is designed to support up to:

(4-6) simultaneous MPEG-2 high-definition video streams

---

### Post by williammanda on 2010-03-01
I finally found the only retailer besides the ruckus site. 

[http://www.expresscasts.com/ruckus/]("http://www.expresscasts.com/ruckus/")

They don't have them listed on the site but they do have them for sale. You have to send an email to:

[email]kyle@expresscasts.com[/email]

---

### Post by williammanda on 2010-03-01
Here's a quote I got:

ExpressCasts LLC
935 Sierra Vista Avenue Suite A    
Mountain View, CA 94043             
Phone:650.964.4569
Fax: 650.964.4783

Name                  Description                    Qty. Unit Price     Discount Line Total
# 901-7811-US00
Ruckus-MediaFlex 7811 Ruckus-MediaFlex 7811 Wireless
Wireless Multimedia   Multimedia Adapter 802.11n (5  1           $199.00                 $199.00 T
Adapter 802.11n (5    GHz) (1 port)
GHz) (1 port)
# 901-7111-US00
Ruckus-MediaFlex 7111 MediaFlex 7111 Wireless
Wireless Multimedia   Multimedia Adapter 802.11n (5  1           $139.00                 $139.00 T
Adapter 802.11n (5    GHz) (1 port)
GHz) (1 port)

---

### Post by williammanda on 2010-03-01
Some information on this product:

[http://www.ruckuswireless.com/products/mediaflex-home-products/7000-series]("http://www.ruckuswireless.com/products/mediaflex-home-products/7000-series")

Select the demo beamflex on the middle right of the page.

[http://www.lightreading.com/document.asp?doc_id=159291&image_number=1]("http://www.lightreading.com/document.asp?doc_id=159291&image_number=1")

This is a slide show of the Ruckus 7811 & 7111 being installed.

---

### Post by williammanda on 2010-03-01
> **svwhisper said:**
> 
>2. Have you had more than one wireless computer accessing data? If so report the >outcome. I was looking at 2 to 3 wireless setups.

As I mentioned above, I can watch HD livetv or recordings on the Acer Revo and a laptop simultaneously without stuttering.  Both are connected to the 7811 via 802.11N 5gHz.  With a single over the air live HD stream, jnettop on the backend reports a 9M bits/second TCP connection to the frontend via wireless.  I don't know if this is accurate or not, but seems about right.
Dave

If possible I would like for you to preform a test. 1st stream one HD video (network show for ABC, CBS, etc...) to one wireless computer and take a reading on the system monitor > network history > sending. This should be something between 15 - 20 Mbs. If the setting is MB, you can change it in edit > preferences > resources. Next continue the 1st stream but start the 2nd stream to another computer and take the same reading. This test should only take 5 minutes at the most.

Next do the same test again but with a dvd video that has been copied to your backend hard drive for each wireless computer.

Finally I would like you to copy a 5GB file, I used a video, from your backend (wired network) to one of the wireless computers and time it till it completes. Also take an average reading, peak reading and any dropouts to zero (using the system monitor > network history > sending) on the backend. Do this for both computers.

What this will give us is the general info for streaming a video and the combined for both computers using HD & dvd video. Also the test will tell us the bit transfer rate and confirm that there is no data rate loss. This is important to verify the Ruckus claim before I purchase.
Thanks

---

### Post by svwhisper on 2010-03-01
The figures I quoted are indeed SNR.  So 20dB SNR for the connection spanning three floors.

I purchased the Ruckus adapters from GeminiComputers.com.  They shipped to Australia without any issue.

Folks, I am not in a position (no time) to run benchmarks on the Ruckus kit so that you can make a purchase decision.  There is a review of the products on tomshardware.com that gave me some confidence the purchase would be worthwhile.

---

### Post by williammanda on 2010-03-02
According to the articles you referred me too. I still have the same questions unanswered.
1. If the 40 - 60 Mbs sustained output for video is all you get then the system will be limited to two computers since HD video will consume up to 20 Mbs.
2. Data transfers will be slower but by how much? According to the article, video gets a higher priority which is sent at a slower rate.

---

### Post by nickrout on 2010-03-02
I suspect the OP is getting good results as a result of the very specific hardware he is using, plus perhaps an element of good luck. I still wouldn't recommend wireless to anyone for a frontend.

---

### Post by svwhisper on 2010-03-03
One point which bears highliting:  The throughput I quoted was over two wireless hops, i.e. backend - switch - wireless client - AP - wireless client - frontend.  I actually think this is pretty impressive.  I would suspect a normal installation would have the backend and AP connected via switch, so only one wireless hop between backend and frontend.

Dave

---

