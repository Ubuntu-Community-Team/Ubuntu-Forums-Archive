---
title: "WandTV USB"
date: 2011-11-17
forum: Multimedia Software
---

### Post by Dooa on 2011-11-17
Hi Guys, 

I'm trying to follow below steps to get Wandtv USB stck ([FONT=verdana]18b4:[/FONT][FONT=verdana]1001[/FONT][FONT=verdana] e3C Technologies[/FONT]
  [FONT=verdana]DUTV007[/FONT]) on Ubuntu 11.04

When I do "[FONT=verdana]**hg clone [http://linuxtv.org/hg/~anttip/ec168/]("http://linuxtv.org/hg/%7Eanttip/ec168/")**[/FONT]"  I get package not available message. 

Can you please help me to find this package?

============================================
[FONT=verdana]First install Mercurial:[/FONT]
  
[FONT=verdana]**sudo apt-get install mercurial**[/FONT]
  
[FONT=verdana]Then get the source for the driver and the v4l and dvb-system with mercurial:[/FONT]
  
[FONT=verdana]**hg clone [http://linuxtv.org/hg/~anttip/ec168/]("http://linuxtv.org/hg/%7Eanttip/ec168/")**[/FONT]
  
[FONT=verdana]**cd ~/ec168/**[/FONT]
  
[FONT=verdana]**make**[/FONT]
  
[FONT=verdana]**sudo make install**[/FONT]
  =============================================

---

