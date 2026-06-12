---
title: "jackd: unknown driver 'alsa'"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by commodore on 2006-06-14
"jackd: unknown driver 'alsa'
12:14:25.888 JACK was stopped with exit status=1.
12:14:28.024 Could not connect to JACK server as client. Please check the messages window for more info."

This is what I get when trying to start jackd. I have an intel_hda card. I don't want to do anything serious but I would atleast like to try.

And I don't have anything listed in the connections window's audio tab.

---

### Post by dolson on 2006-06-15
Have you tried deleting the ~/.asound* files? This was an issue we had early on in the Dapper beta process, and it was posted in there and that was the solution. If that doesn't work, I am not sure..

---

### Post by commodore on 2006-06-17
I don't have that folder :S And I installed Dapper Flight 7 at first.

---

### Post by tmoneygetpaid on 2006-09-18
Hope this bumps to where someone actually sees it.

Anyway, I am having the same problem. I found the "asound" directory under /proc/asound.

Do I just delete all the contents of this directory?

Thanks.

---

### Post by commodore on 2006-09-19
Someone on this forum sent me an e-mail to delete some file and it worked. Too bad I can't remember the name of the file and of course I deleted the e-mail.

---

### Post by tmoneygetpaid on 2006-09-19
bah.... well thanks. If anyone has this info, it'd be much appreciated if you posted.

Thanks again.

---

### Post by dolson on 2006-09-19
As I said in my other post in this thread, delete ~/.asound*

As in:

rm -rf ~/.asound*

---

### Post by tmoneygetpaid on 2006-09-19
unfortunately, that didn't work.

advice appreciated.

---

### Post by Dr.Who on 2006-09-19
alsa is not working here too after recent kernel update. It worked well before. Non Alsa sound still works but jackd cant start.

---

