---
title: "Wireless for Mythtv using Ruckus Wireless"
date: 2011-07-28
forum: Mythbuntu
---

### Post by williammanda on 2011-07-28
I recently was forced into changing my wired Mythtv network over to wireless. After all the research was done I basically decided the only way to do this was by using Ruckus Wireless. There were 2 reasons for not using a N wireless system. The first was that linux is always lagging behind in implementing the latest devices ie adapter drivers. Second was the N wireless system itself, there are to many variables ie distance, obstructions, signal strength, etc... I'm going to document as well as possible my trip down "Ruckus lane".
Today I received two components that make up a basic connection.

MediaFlex 7811 multimedia access point
MediaFlex 7111 multimedia Wi-Fi adapter

These two devices basically replace the cat 5 / 6 cable. You plug the 7811 into the router and the 7111 into the NIC of the computer. This is great for linux since there are no drivers involved, it's transparent.

The overall plan is to connect four Mythfrontends wireless. To accomplish that I will be employing two 7811's and each 7811 will have two 7111's.

1st Test
After setting up the 7811 and a 7111 I decided to run a capacity test to see the overall bandwidth. I placed both devices one room apart. I copied a large file and got an average 90Mbps. One interesting note, one of the benefits of Ruckus is that it constantly adjusts for the optimum signal. I started out with the 7111 up about 5' and then moved it to the floor. During this time the signal dropped during the movement but went right back to the average 90Mbps. Next I setup Mythtv to play about 10 hours of HDTV. One of the test HDTV recordings I use averages 18 Mbps. I will report back tomorrow.

---

### Post by williammanda on 2011-07-28
Test 1 continued
I ended up running almost 20 hours of HDTV recordings without a problem. I will continue this test throughout since the adapter is on the frontend in the livingroom.

Test 2
This test was aimed at distance. I used a windows laptop with XBMC. Since XBMC streams video I could measure the largest capacity that Ruckus would allow at a given distance.
All locations are referencing the 7811 Access point ( which is by the router ) and the 7111 adapter ( which is with the laptop ). The first number is horizontal distance and the second is vertical distance ( which is always down ).

Location 1
20' x 10' @ 55 - 60 Mbps
Location 2
20' x 20' @ 45 - 50 Mbps
Location 3
16' x 30' @ 45 - 50 Mbps
Location 4
45' x 10' @ 42 - 47 Mbps

The test at location 4 was double the horizontal distance of location 1 with some reduction. The tests at locations 2 and 3 were about the same with location 3 being 10' lower. This test lasted about 5 minutes at each location. Using Mythtv the same video averaged 3 Mbps.

---

### Post by williammanda on 2011-07-30
A benchmark going forward, having four frontends working receiving a HDTV recording, the server is sending out an average of 55 Mbps.

So far the one frontend with Ruckus wireless is working fine ( my wife hasn't noticed the difference ).

---

### Post by williammanda on 2011-08-02
Test 1 update:
The livingroom 7111 has performed flawlessly. There haven't been any issues (artifacts, freezing, etc...). Again I can't tell any difference using Ruckus verses wired for Mythtv.

Test 3
I now have three 7111's and still just one 7811. This test will evaluate the bandwidth usage of the 7811 going to three 7111. 

Remember that I tested transferring a large file and averaged 90 Mbps. Basically the 90 Mbps ended up getting divided between all three 7111's. The transfer rate ranged on all three but the sum of each 7111 Mbps equaled the total 90 Mbps average.

Next I applied the same test with the HDTV recording and received the same result as the file transfer test. I will continue to test the three frontends with the 7111's and report the progress

Note:
The 7811 basically equals a 100 Mb network card.

---

### Post by williammanda on 2011-08-12
Test 1 update:
The Livingroom unit still preforms as well as a wired system. I still can't tell any difference. Watching recorded video or live tv or recorded tv works flawlessly. 

Test 3 update:
The use of the three frontends hasn't shown any problems using mythtv. I haven't monitored the use of all three frontends continuously but the use of the three over this time hasn't shown any problems. Obviously using one 100Mb connection has it's draw backs between three computers. I can't expect to transfer files at a 100Mb rate when using three computers.

Note:
The Ruckus system will prioritize video over data. Which means if I have one frontend streaming video and one transferring data or a file...the video stream will be the number one priority. The video stream will be the highest priority and will maintain bandwidth for the video.

---

### Post by williammanda on 2011-08-12
I want to talk about Ruckus wireless support.

The support is mainly email (support@ruckuswireless.com) but you can call 650-265-4200 and get a live person. My experience has been that the live support is no better than email. The support isn't as well versed in the home use as the commercial. Also I bought a mix of new and used products. You get a one year warranty on the new product and get the availability of firmware updates for life, on the website. I found that the used products work fine but you may not get proper response, 24 hour if you have a current product, verses a two week response for used.

If anyone decides to use this product I will be  happy to provide whatever support I can. Please contact me by private message. 

I feel this product is far superior than the current "N" wireless and recommend it's use for Mythtv.

---

### Post by williammanda on 2011-08-22
Test 3 update:
The three frontends operating off one 7811 continued to work well. 

Final application:
The original setup was to have four frontends but there are only three at the moment. Now I have two 7811's. One 7811 with one 7111 and the other 7811 has two 7111's. Also I have a network printer connected. 

Final thoughts:
The Ruckus system has met and exceeded the original intent. I'm very pleased with the results, to put it simply, you can't tell the difference between wired or Ruckus.

---

