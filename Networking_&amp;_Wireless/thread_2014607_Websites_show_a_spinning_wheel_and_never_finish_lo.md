---
title: "Websites show a spinning wheel and never finish loading"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by riyas786tk on 2012-07-02
i cant access some websites in my ubuntu 12.04 like thegeekstuff.com and yahoo.com. Such specific websites (not all) start to load, but never finish (i.e. the tab displays a spinning wheel and "Connecting..." for several minutes).
I tried this in both firefox and google chrome. But still the same.
But these specific sites can be accessed in my windows 7 platform.

please suggest something to fix this..
thanks

---

### Post by sanderj on 2012-07-02
Open a terminal (in the Dash, type "terminal", then click on the Terminal logo).

In the terminal, type "time wget yahoo.com". Post the output here

---

### Post by vasa1 on 2012-07-02
Are you using the same browsers with the same add-ons on both platforms?

---

### Post by riyas786tk on 2012-07-02
> **sanderj said:**
> Open a terminal (in the Dash, type "terminal", then click on the Terminal logo).

In the terminal, type "time wget yahoo.com". Post the output here

riyas@riyas-desktop:~$ time wget yahoo.com
--2012-07-02 20:20:41--  [http://yahoo.com/](http://yahoo.com/)
Resolving yahoo.com (yahoo.com)... 98.139.183.24, 209.191.122.70, 72.30.38.140
Connecting to yahoo.com (yahoo.com)|98.139.183.24|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.yahoo.com/](http://www.yahoo.com/) [following]
--2012-07-02 20:20:43--  [http://www.yahoo.com/](http://www.yahoo.com/)
Resolving [www.yahoo.com](www.yahoo.com) ([www.yahoo.com](www.yahoo.com))... 106.10.170.118, 2406:2000:fc:200::c:9102, 2406:2000:fc:200::c:9103
Connecting to [www.yahoo.com](www.yahoo.com) ([www.yahoo.com)|106.10.170.118|:80](www.yahoo.com)|106.10.170.118|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://in.yahoo.com/?p=us](http://in.yahoo.com/?p=us) [following]
--2012-07-02 20:20:43--  [http://in.yahoo.com/?p=us](http://in.yahoo.com/?p=us)
Resolving in.yahoo.com (in.yahoo.com)... 106.10.170.118, 2406:2000:ac:8::c:9101
Reusing existing connection to [www.yahoo.com:80](www.yahoo.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.1'

    [         <=>                                     ] 173,211     69.6K/s   in 2.4s    

2012-07-02 20:20:46 (69.6 KB/s) - `index.html.1' saved [173211]


real	0m5.086s
user	0m0.000s
sys	0m0.012s

---

### Post by riyas786tk on 2012-07-02
> **vasa1 said:**
> Are you using the same browsers with the same add-ons on both platforms?
yes. i am using the google chrome in both my platform.

---

### Post by sanderj on 2012-07-02
So, firefox and chrome never work for yahoo.com, and wget works?

Really strange.

Do you use plugins / extensions? Easy check: create another account on your Ubuntu, login under that account, and start Chrome  to see whether yahoo.com is reachable.

Or, easier, run this from your command line:

chromium-browser --disable-extensions

---

### Post by vasa1 on 2012-07-02
> **sanderj said:**
> ...
Or, easier, run this from your command line:

chromium-browser --disable-extensions
You mean **google-chrome** --disable extensions ?

---

### Post by vasa1 on 2012-07-02
Plus there are the usual trouble-shooting steps:
delete cookies, empty cache, try a new profile.

---

### Post by sanderj on 2012-07-02
> **vasa1 said:**
> You mean **google-chrome** --disable extensions ?

No, I meant what I wrote. That's what works on my system (Ubuntu 12.04).

---

### Post by vasa1 on 2012-07-02
> **sanderj said:**
> No, I meant what I wrote. That's what works on my system (Ubuntu 12.04).
But OP is using google-chrome.

---

### Post by sanderj on 2012-07-02
> **vasa1 said:**
> But OP is using google-chrome.

OK. I'm not sure what the OP means with that: maybe it is Google Chrome, maybe it is Chromium (because that is easier to install on Ubuntu). I often say "I use Chrome", whereas it is Chromium.

Let's wait for the OP's reaction

---

### Post by dandygrow on 2012-10-31
OP has left but I am still getting the same problem.

---

