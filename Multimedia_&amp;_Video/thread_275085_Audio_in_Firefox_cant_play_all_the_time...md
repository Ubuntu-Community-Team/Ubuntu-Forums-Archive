---
title: "Audio in Firefox cant play all the time.."
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by astronerd on 2006-10-10
Hi all, I am running dapper, all updates and I am having an issue with firefox.  If I am listening to an mp3 on xmms, and I want to listen to a video from youtube, or something like that, there is no sound from firefox after I turn off the music from xmms.  So I have to restart firefox to get the music to play..  Is this firefox's fault, my audio card, or some combo?
thanks, 
CM

---

### Post by divague on 2006-10-10
try this, it might help you

install alsa-oss and edit this file /etc/firefox/firefoxrc

change:

FIREFOX_DSP=""

for 

FIREFOX_DSP="aoss"

---

### Post by astronerd on 2006-10-10
Thanks,  So I installed aoss and edited that file and saved it..  Restarted firefox, played a song on xmms and then went to you tube.  opened a video, and turned off the song from xmms, but I still got no sound from the video.  Is there anything else I needed to do? Thanks
CM

---

