---
title: "GSM Airprobe Error"
date: 2014-05-14
forum: Mobile Technology Discussions (CLOSED)
---

### Post by telenoobie on 2014-05-14
Hi,

I'm recently new to telecommunications, and I have been having difficulty with some of the python scripts within gsm-receiver of airprobe. Everytime I run the scripts ./go_usrp2.sh <file> I get the following output and error (I am trying to run the test from these sites: [[COLOR=#dd4814]http://lynxnuzlan.wordpress.com/2011...ncryption-a51/[/COLOR]]("http://lynxnuzlan.wordpress.com/2011/02/23/practical-exercise-on-the-gsm-encryption-a51/") and [[COLOR=#dd4814]https://srlabs.de/airprobe-how-to/[/COLOR]]("https://srlabs.de/airprobe-how-to/"))

>>> gr_fir_ccc: using SSE
>>> gr_fir_ccf: using SSE
Key: '0000000000000000'
Configuration: ''[INDENT]No configuration set.[/INDENT]
configure_receiver
Traceback (most recent call last):
[INDENT]File "./gsm_receive100.py", line 119, in <module>[/INDENT]
[INDENT=2]main()[/INDENT]
[INDENT]File "./gsm_receive100.py", line 114, in main[/INDENT]
[INDENT=2]gsm_receiver_first_blood().run()[/INDENT]
[INDENT]File "./gsm_receive100.py", line 47, in __init__[/INDENT]
[INDENT=2]self.connect(self.source, self.filtr, self.interpolator, self.receiver, self.converter, self.sink)[/INDENT]
[INDENT]File "/usr/local/lib/python2.7/dist-packages/gnuradio/gr/top_block.py", line 124, in connect[/INDENT]
[INDENT=2]self._connect(points[i-1], points[i])[/INDENT]
[INDENT]File "/usr/local/lib/python2.7/dist-packages/gnuradio/gr/top_block.py", line 128, in connect[/INDENT]
[INDENT=2](dst_block, dst_port) = self._coerce_endpoint(dst)[/INDENT]
[INDENT]File "/usr/local/lib/python2.7/dist-packages/gnuradio/gr/top_block.py", line 139, in _coerce_endpoint[/INDENT]
[INDENT=2]raise ValueError("unable to coerce endpoint")[/INDENT]
ValueError: unable to coerce endpoint


Thanks for your help :)

---

