---
title: "Can you play this video?"
date: 2008-09-16
forum: Multimedia Software
---

### Post by heatpumpcontrol on 2008-09-16
I'd like to play videos from this site but I keep getting a request to download a plugin which is never available.... I'm guessing it's a flash plugin but I'm not sure...

[http://joox.net/cat/1104/id/222/source/1]("http://joox.net/cat/1104/id/222/source/1")

If you can play it, what settings do you have or what is it you have that I don't?

thanks

---

### Post by howefield on 2008-09-16
joox.net uses the DivX plugin, in Firefox, go to tools > addons > plugins, is it listed there ?

---

### Post by heatpumpcontrol on 2008-09-16
> **howefield said:**
> joox.net uses the DivX plugin, in Firefox, go to tools > addons > plugins, is it listed there ?

Yes I do I  have that listed in the plugins section...

---

### Post by heatpumpcontrol on 2008-09-16
Is everyone else able to view this clip? ... I'd just like to know....

---

### Post by mexlinux on 2008-09-16
I can't see it, looking at the page source this what calls the video:

```
<script type="text/javascript">
        /*<![CDATA[*/
          PutStreamPlug(720,397);
          StreamPlugSetBKColor(0,0,0);
          StreamPlugLoadUrl('http://diffuser4.messagefromme.com:1060/myvideoregistry/video_11381.ogm');
          StreamPlugResizeVideo(720,335);
        /*]]>*/
        </script>
```

---

### Post by namaster on 2008-10-25
I am also having problem to watch joox videos. Any idea how i can see it? I do have divx plugin still it stays no plugin?

Any help would be gr8!

---

### Post by ciscosurfer on 2008-10-25
If your flash is enabled, go here: [http://www.youtube.com/results?search_query=pink+floyd+goodbye+blue+sky&search_type=&aq=0&oq=pink+floyd+goodbye](http://www.youtube.com/results?search_query=pink+floyd+goodbye+blue+sky&search_type=&aq=0&oq=pink+floyd+goodbye)

---

### Post by ruien on 2008-10-25
In firefox type about:plugins and see if you have the mplayer plugin enabled. If so wich version? Most likely you'll have 3.50 wich is standard ubuntu version for 8.04. It should work but you can get the 3.55 plugins from Mepis repo and just copy them over your /usr/lib/mozilla/plugins and it should do the trick. I have no problems playing divx video but i needed another version of mplayer plugin because quicktime didnt work properly on apple.com. 


Hope this can help you out. :)

---

### Post by kerry_s on 2008-10-25
[http://www.streamplug.com/StreamPlug/ns-installation/eng/index.html](http://www.streamplug.com/StreamPlug/ns-installation/eng/index.html)

never mind, it says linux version coming soon, i don't think it's here yet. i did not try that download.

---

