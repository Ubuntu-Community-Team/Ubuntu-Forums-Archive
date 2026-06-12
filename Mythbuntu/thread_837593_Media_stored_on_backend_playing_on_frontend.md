---
title: "Media stored on backend playing on frontend"
date: 2008-06-22
forum: Mythbuntu
---

### Post by Thingie on 2008-06-22
Hi,

I recently installed Mythbuntu as a back/frontend on one pc and as (disked) frontend on another pc. The databae is running fine and I can connect correctly from my frontend. I have a lot of media stored on my backend, movies (divx), dvd's (iso) and music (mp3). I added the folders on the backend and the media is displayed in my media library on the backend. When i look at the media library on the frontend it stays empty. I searched the forum and the internet but can't find an answer. I looked at my settings but can't find nothing. Anybody an idea?

Thx

Thingie

---

### Post by uMuppet on 2008-06-22
When using NFS and Mythvideo on multiple frontends, it helps to have both video locations mounted at the same absolute path. (IE, all your videos should either reside in or be symlinked to the same dir on all machines (ie /var/lib/mythtv/videos))

So make sure you have the same path to your videos folder on your frontend as you do on your backend.  

I spent a while trying to get this right too.  Another thought too, if you are using the standard place for your posters they will not show up on your frontend.  You will need to either share your posters folder or move it to within your videos folder.

---

### Post by chenqinbo5 on 2008-06-22
do drop by to [www.shop-foco.com](www.shop-foco.com) <http://www.shop-foco.com>  look through the articles there. With information on anything from getting the  cheapest shoes, you'll find something that helps you save a lot of money.
-- 
the cheapeast shoes
[www.shop-foco.com](www.shop-foco.com)
<msn:shop-foco@hotmail.com>
E-mail:shopfoco@gmail.com
Thank you for your E-mail and your order

---

### Post by Archmage on 2008-06-23
Did you enalbe the automatical scanning for new contents? Did you allow the extension?

---

### Post by freymann on 2008-06-23
This url may be useful for you too:

[http://www.mythtv.org/wiki/index.php/Mediashares](http://www.mythtv.org/wiki/index.php/Mediashares)

---

