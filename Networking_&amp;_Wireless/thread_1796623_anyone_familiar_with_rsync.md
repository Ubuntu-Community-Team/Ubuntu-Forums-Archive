---
title: "anyone familiar with rsync?"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by beterhans on 2011-07-04
I have a Ubuntu PC as my Home server
and a Macbook as my laptop. 

I hope I can use rsync to sync all documents, thunderbird mails and iTunes library with the server.

My goal is do a 2 way sync
Always find and keep all file as the latest version. find and delete the file I've deleted. 

it looks like rsync is the cheapest way can do it.
but rsync have too much options I really can't understand it well.


and I have another 2 questions
1. could rsync do a 2 way sync?  the cli looks only 1 way
2. it have too many delete options. what's the different? or which one I should use?


thank you

---

### Post by aeiah on 2011-07-04
```
rsync -an --delete --progress /path/to/source/ username@destination:~/path/to/destination/

```

-a : archive
-n : dry run (ie, it wont actually do anything until you run the command without the 'n')
--delete : removes files on the destination which are no longer on the source

by 2 way sync, i assume you mean if you make changes on the server, they get synced back to the macbook? this doesn't really work with rsync. ive used unison for this task and it works great, but ive only done it linux to linux. there is a mac version though. unison more or less behaves the same way as rsync but it is bidirectional.

---

