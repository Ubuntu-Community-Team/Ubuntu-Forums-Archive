---
title: "Mythweb on Hardy not displaying video thumbnails"
date: 2008-04-28
forum: Multimedia Software
---

### Post by fieldyweb on 2008-04-28
I've installed MythTV, and its working fine, however i have one niggling issue, i've added the mythweb plugin, which works, and has secuity, just won't show the thumbnails. I have setup the symlins, however they keep coming back with missing cover, after a bit of diagnosis, i think its the underlying code causing the issue.


> 
iv id="40" class="video" onmouseover="video_popup(this.id)" onmouseout="hovering_video_id = null;">
        <div id="40_categoryid" class="hidden">0</div>
        <div id="40_genre" class="hidden"> 4 </div>
        <div id="40_browse" class="hidden">1</div>

        <div id="40-title" class="title"><a href="/mythweb/data/video/Movies/SciFi/2001.a.space.odyssey.avi">2001: A Space Odyssey</a></div>
        <div id="40_img">                <img src="**_data/video_covers//0062622.jpg_**" width="88" height="140" alt="Missing Cover"></div>
        <div id="40-category">           Uncategorized</div>
        <div id="40_playtime">           2 hrs 21 mins</div>
        <div id="40_imdb">               <a href="http://www.imdb.com/Title?0062622">0062622</a></div>

The Highlighted section for the image above shows data/video_covers**//**0062622.jpg and i think its the // which is causing the issue.

Can anyone tell me where i can edit this setting?

---

