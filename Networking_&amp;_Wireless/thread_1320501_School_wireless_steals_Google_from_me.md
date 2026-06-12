---
title: "School wireless steals Google from me"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2009-11-09
This doesn't directly relate to Ubuntu, but I figure you folks are so smart you may be able to help me out anyway.

At school we have a wireless system that requires you to log in in order to gain access to the internet.  My homepage is Google, so when the browser opens, it attempts to load Google, but is redirected to the authentication page.  From that moment on, anytime I hit the home button, or type [www.google.com](www.google.com) into Firefox, I get redirected to their splash screen page.

If I completely disable the history, it stops doing this, but I need the history, at least for the day, as I use the laptop for research and often have a "oh wait, that useless article WOULD be hand to have after all!" moment.  Anyway, has anyone else experienced something similar and is there a way to get that system from stealing Google from me?  

Thanks

JTS

---

### Post by Thirtysixway on 2009-11-09
It sounds to me like your school is using custom dns servers.  DNS is what translates [www.google.com](www.google.com) into an IP address.  What your school can do is make it so if you type in [www.google.com](www.google.com), instead of turning up its real IP it gives an IP for the splash page.

(Sometimes you can use this method to get past wireless points that make you pay :p) but if it really bothers you, once you connect to the network just change the DNS servers.  [http://www.opendns.com](http://www.opendns.com)

Just as a warning, if there are intranet sites (only accessble from inside your schools network) this will break that access.

Now this may not be the case.  You may be running through a proxy, which could be more difficult to get around depending on the setup.

---

### Post by lensman3 on 2009-11-09
It used to be if you used the IP address of one of the google.com translation sites, you could get to the full google search engine.  What I mean by translation site is googles site that translates from say "German" to "English".  To get this to work you first had to get the IP address of the translation site from a home computer, have google translate a "German" site, and then use that number at school.

Once you got to the translation site, different DNS servers were used.

Hope this helps.

---

### Post by chili555 on 2009-11-09
In Firefox, if you Edit -> Preferences -> Main and change your home page from [http://www.google.com](http://www.google.com) to [http://74.125.157.104](http://74.125.157.104), does the behavior change?

---

### Post by jimmy the saint on 2009-11-10
I have been playing around with it and I am convinced that it has nothing to do with DNS.  It has to do with the way that Firefox handles its history.  The only thing that fixes it is to completely disable history.  The funny thing is that if I use the Google search bar, since the url is slightly different, I get Google just fine.  Sometimes I can then click the Google logo and get to Google.  

I appreciate the tips.  

Thanks

JTS

---

### Post by fargle on 2009-11-10
Have you tried hitting CTRL-F5 to refresh the page?  That should definitely reload it without hitting the cache once you're past the login.

The other thing I always do for these is go somewhere I don't care about instead of Google - I use yahoo.com because I never go there.  This requires another setting I always use, though, which is to tell Firefox to start on a blank page instead of loading a home page, I think that's a waste of bandwidth anyway.

---

### Post by JCoster on 2009-11-10
Try changing your 'browser.cache.check_doc_frequency' in about:config.  If you change it to '1' then it checks for an updated version everytime a page is loaded, else you may want to try '0' to do it once per session.

Check [this](http://kb.mozillazine.org/Browser.cache.check_doc_frequency) out.

---

### Post by underquark on 2009-11-10
Since you use a laptop all day, that means you generally use the same computer for all your browsing, does it?  In that case, why not create your own custom homepage?  I have one that is simply a html file with a table with a half-dozen categories such as "Searches", "Entertainment", "Computing" ... and each category (or column in the table) has several links beneath it.  You can jazz it up with  nice background and a few pictures if you must.

---

