---
title: "[SOLVED] MYTHWEB defaults gone after browsing site with blackberry web browser"
date: 2008-05-27
forum: Mythbuntu
---

### Post by adubas on 2008-05-27
Strange problem that has happend two times now and I don't know how to fix.

Normally when I go to mythweb, I have a robust page with graphical listings and options etc. I went to my mythweb site with my blackberry browser (I got a txt version of mythweb) and now when I log into my mythweb site from a normal computer web browser, I only receive a txt version of the site. I cleared local cache, tried firefox etc. I am unable to get old version of mythweb site back. 

The first time this happened, I rebuilt my whole box (not for this reason) and on the new build it was back to normal. So yesterday, I went to my site with my blackberry and now its back to serving only txt version of mythweb to all clients no matter the browser type...

How do I get it back to being normal??

---

### Post by freymann on 2008-05-27
> **adubas said:**
> 
Normally when I go to mythweb, I have a robust page with graphical listings and options etc. I went to my mythweb site with my blackberry browser (I got a txt version of mythweb) and now when I log into my mythweb site from a normal computer web browser, I only receive a txt version of the site. I cleared local cache, tried firefox etc. I am unable to get old version of mythweb site back. 


Try adding '?RESET_TMPL=true' to the end of a mythweb URL and it
should reset the template."

This thread has details:

[http://ubuntuforums.org/showthread.php?t=761093&highlight=mythweb]("http://ubuntuforums.org/showthread.php?t=761093&highlight=mythweb")

---

### Post by adubas on 2008-05-27
THAT DID THE TRICK!!! :p

Thanks!!!

---

