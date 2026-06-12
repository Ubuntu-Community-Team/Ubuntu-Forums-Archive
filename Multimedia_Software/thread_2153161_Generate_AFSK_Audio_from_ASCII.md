---
title: "Generate AFSK Audio from ASCII"
date: 2013-06-10
forum: Multimedia Software
---

### Post by mnelson01 on 2013-06-10
Has anyone come across a program (preferrably command line) that will take ASCII, transform it to binary and then generate AFSK (Audio Frequency Shift Keying) and save it to a file?

I need some pretty specific frequencies for the binary (must use Audio Frequency Shift Keying at a rate of 520.83 bits per  second to transmit the codes. Mark frequency is 2083.3 Hz and space  frequency is 1562.5 Hz. Mark and space time must be 1.92 milliseconds.  Characters are ASCII seven bit characters as defined in ANSI X3.4-1977  ending with an eighth null bit (either 0 or 1) to constitute a full  eight-bit byte), so I'm looking for something pre-developed for the U.S. Emergency Alert System (EAS), or something with enough flexibility to do this.

---

### Post by sanderj on 2013-06-10
At first I thought "Baycom", but considering all specs you give: have you looked at GNU Radio?

EDIT: I don't know if GNU Radio can module signals, or only demodulate...

---

