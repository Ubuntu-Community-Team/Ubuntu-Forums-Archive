---
title: "chromium space bar inconvenience"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by I'mGeorge on 2010-11-29
The problem it's that on some web sites in chromium while I'm trying to type and use the space bar the page scrolls down. Now I know using space bar scrolls down and shift+space bar scrolls up but this it's pretty annoying when you have to type something either.

Any ideas in how can I disable this scroll up/down chromium-browser shortcuts ?

---

### Post by I'mGeorge on 2010-11-29
Huh and I thought this would be something really easy. Isn't there some sort of a configuration file that I've didn't observed where you could setup the keys for chromium ?

---

### Post by TBABill on 2010-11-29
I've never seen that happen. But if it only happens in Chromium I'd be led to believe it is something in its configuration and not something Ubuntu specific. Will do some searching.

---

### Post by TBABill on 2010-11-29
[http://code.google.com/p/chromium/issues/detail?id=49218](http://code.google.com/p/chromium/issues/detail?id=49218)
 
Obviously you aren't using Arch but the behavior seems to mirror what was reported there.

---

### Post by I'mGeorge on 2010-11-29
> **TBABill said:**
> I've never seen that happen. But if it only happens in Chromium I'd be led to believe it is something in its configuration and not something Ubuntu specific. Will do some searching.

I'm using Debian. But the thing it's if I'm in a live chat room, sharing some opinions about global warming when I want to press space between words it scrolls down either. This doesn't happens for example when I'm typing this current reply. In iceweasel(firefox) there's no problem so I'm inclined to believe it's something about chromium. Anyway this it's rather a small bug and I still like chromium more than firefox :-) But a fix for this inconvenience would be really nice.

---

### Post by I'mGeorge on 2010-11-29
I've found some sort of a fix. Googleing a little bit about this problem I found this code in javascript

```

window.onkeydown=function(e){ 
if(e.keyCode==32){ (32 it's the keycode for space bar)
return false; 
} 
};

```

So I thought I could store the code into a spacebar.js file and try making an extension for chromium. For an extension to be accepted by chromium you have to make a manifest.json file, so I've made something like this

```

{
  "name": "RemSPC",
   "content_scripts": [
    {
      "run_at": "document_start"
      "js": ["spacebar.js"]
    }
  ],
}

``` 

after reading some instruction from their site [http://code.google.com/chrome/extensions/content_scripts.html](http://code.google.com/chrome/extensions/content_scripts.html)
But I get a syntax error at line 6 column 7. So anyway I'm still working at it, but any suggestions would be great.

---

### Post by I'mGeorge on 2010-12-04
okey, problem solved. Install this extension for chromium [https://chrome.google.com/extensions/detail/mgjjeipcdnnjhgodgjpfkffcejoljijf?hl=en](https://chrome.google.com/extensions/detail/mgjjeipcdnnjhgodgjpfkffcejoljijf?hl=en) It's a shortcut manager, in this way you can define any shortcuts for chromium and you can override the space bar function to scroll up or down by 0 pixels, so in the end it won't scroll at all.

---

### Post by onaridge on 2010-12-06
So THAT's what was happening. It's been driving me crazy for weeks. Thank you!!!!

---

### Post by smoosh on 2011-03-18
Thank you!

---

