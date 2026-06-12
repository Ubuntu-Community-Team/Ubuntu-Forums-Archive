---
title: "unsteady RSS feed underneath video script problem?"
date: 2012-10-22
forum: Multimedia Software
---

### Post by vtimp1 on 2012-10-22
Underneath a video we are trying to stream an RSS-feed. This is working however the feed is not running smoothly at all. The hight of the feed fluctuates and the text is displayed very unsteadily. 

Underneath you can see the RSS-part of the script we are using. We are using ubuntu. 


Does anybody have any suggestions? Thanks very much in advance. 

# define RSS
rss_enabled=1
rss_enabled_channel[1]=1
rss_enabled_channel[2]=0
#sout_mux_caching=10000
sout_mux_caching=0
#rss_font="/usr/share/fonts/Type1/gsfonts/a100131.pfb"
rss_font="/usr/share/fonts/truetype/ttf-lucida/lucidatypewriterbold.ttf"
rssurl="http://www.nu.nl/feeds/rss/algemeen.rss"
rss_local_url="http://127.0.0.1/rss/" # NIET VERANDEREN!
rss_x=0
rss_y=23 #hoogte hoger is hoger
rss_color=16777215
rss_length=45
rss_size=20
rss_position=8
rss_opacity=255
rss_speed=80000 # hoger is langzamer
rss_ttl=600
rss_title=0
rss_images=0

---

