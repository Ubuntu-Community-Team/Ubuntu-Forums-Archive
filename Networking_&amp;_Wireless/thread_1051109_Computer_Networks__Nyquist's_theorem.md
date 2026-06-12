---
title: "Computer Networks : Nyquist's theorem"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by tavati on 2009-01-26
am reading a book by Tanenbaum on computer networks. i have some basic doubt about the max. data rate(MDR).

the eq'n is : MDR = 2H * log 2 (V) samples per second

Now the bold lines are from other texts which i got by some searching.

[B][I]if V uses m bits then MDR = 2H * log 2 (2^m) bits per second
= 2H * m[/I][/B]

However, a line in this( Tanenbaum's) book on page 127 says, " if the symbol consists of 0 volts for a logical 0 and 1 volt for logical 1, the bit rate 2400bps. ( at a baud of 2400 bauds). if, however, if the voltages 0,1,2,3 are used, every symbol consists of 2 bits, ...... data rate of 4800 bps.

this last example of four voltages does not gel with the concept(bold letters above). it has to be other way i.e. if we choose 2 bits to form a symbol, then there will be four symbols and hence four levels . 

rest all fits in but why Tanenbaum wrote like this ?

---

### Post by puppywhacker on 2009-01-26
I think you are confused on the meaning of symbol. You said 4 symbols are 4 levels, but that is incorrect.

One symbol has 4 levels. these levels correspond to a 2 bit value 

0 Volts = 00
1 Volts = 01
2 Volts = 10
3 Volts = 11

so if you put 2 volts on the wire, it represents the bits "10" ... one symbol contains 2 bits

---

