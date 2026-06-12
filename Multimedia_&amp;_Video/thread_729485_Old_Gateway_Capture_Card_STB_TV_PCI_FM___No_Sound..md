---
title: "Old Gateway Capture Card STB TV PCI FM   No Sound."
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by h2gofast on 2008-03-19
STB TV PCI FM, Gateway P/N 6000704 (bt878) Capture Card

I've searched to no avail.
And I've tried everything I could find.  The card works with tvtime, but no sound.
Sound works with every other application.  No sound from the capture card though.
Any help would be appreciated before I throw in the towel.

I've changed modules.conf twice 
First time: 
#STB Gateway OEM Bt848 TV/FM Tuner
bttv card=3 tuner=2 radio=1
tvaudio tea6300=1 tda9855=0 tda9850=1

Second Time:
# i2c
alias char-major-89 i2c-dev
options i2c-core i2c_debug=1
options i2c-algo-bit bit_test=1

# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
options bttv  card=40 radio=1 bttv_verbose=2
options tuner  debug=1 type=2
options tvaudio  debug=1 tda9850=1
options tvmixer  debug=1 devnr=1
pre-install bttv (/sbin/modprobe "tuner"; /sbin/modprobe "tvaudio"; \
                  /sbin/modprobe "tda7432"; /sbin/modprobe "tvmixer")
post-remove bttv (/sbin/modprobe -r "tuner"; /sbin/modprobe -r "tvaudio"; \
                  /sbin/modprobe -r "tda7432"; /sbin/modprobe -r "tvmixer")


Neither enabled sound

---

