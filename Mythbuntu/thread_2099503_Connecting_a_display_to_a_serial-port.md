---
title: "Connecting a display to a serial-port"
date: 2012-12-29
forum: Mythbuntu
---

### Post by whocares02 on 2012-12-29
I bought a silverstone lc20 case and unfortunately it comes without the vfd-display which is only shipped with the extended version of the case. I found out that it gets produced and sold by soundgraph but ordering it directly from korea is far too expensive.

Therefore I'm about to install a similar display on my own. My question is: How? 

The mainboard provides a serial-header and no parallel port. Many VFD-Displays offer support for standards like **RS232** and **CMOS synchronous serial** (e.g. [this one]("http://noritake-vfd.com/cu16025-uw6j.aspx")). They both mean the computer's serial-port, as I figured out using google. The protocol-standard often used is called HD44780 which is supported by mythbuntu's lcdproc-driver. 
However, I just can't find any kind of data-sheet or drawing telling me how to connect such a display to my mainboards serial-port. USB-displays on the other hand are hard to find. Manufacturers like crystalfontz don't produce them in the size I need anyway. Most displays are for parallel or serial-ports.

**Edit:** I found [a forums-post by someone]("http://www.exclaim.de/forum/post/96072/LCD-Anschlussplan.html") connecting a device to the parallel-port. The post shows the kind of diagram I am looking for - just showing the wiring of a vfd-serial-port-connection instead.

---

### Post by milhouse on 2012-12-31
All RS-232 compatible serial displays will have an Rx and Ground input which you will need to connect to the Tx pin and Ground pin on your mainboard. Your mainboard's manual should give you the pin-out of the header. The display will also have a default baud rate which you'll use when you configure whatever ultimately will talk to it.

The display of course will have a power input pin as well. If it is a common (3.3v,5v,12v) you can get that from your PC's power supply.

Sorry this is a short answer but I am running out the door (Happy New Year!) but I'll check back and answer as I can.

---

### Post by dc_wmj2 on 2013-01-01
The mainboard-manual describes the serial-header this way.

```
 Pin   Signal-Name       Pin    Signal-Name 
  1     DCD               2      RXD# 
  3     TXD#              4      DTR 
  5     Ground            6      DSR 
  7     RTS               8      CTS 
  9     RI               10      Key (no pin)
```

This pin-assignment matches with the one I found [on wikipedia]("http://en.wikipedia.org/wiki/Serial_port") for the pin-assignment of 9-pin-serial-ports.

Unfortunately the [Noritake CU16025-UW6J]("http://www.noritake-elec.com/uversion.htm")supports synchronous serial but seems to use a different pin-assignment. The names don't match. The data-sheet can be found [here]("http://uk.farnell.com/noritake-itron/cu16025-uw6j/vfd-module-2x16-5mm/dp/1495416"). They write about data channel 1-6. Where should I connect them to? Isn't that driver-dependent? I didn't find any wiring-diagrams on the LCDProc-homepage.

---

### Post by milhouse on 2013-01-01
I will add that CMOS synchronous serial is not the same as RS-232 serial. This [link]("http://www.noritake-elec.com/interfaces/cmos_synchronous_serial.htm") shows a data line (Sin), a clock line (Sclk), and a busy line (Sbusy). Not shown is a ground line which would be required. From the name we also assume these operate at CMOS signal levels, not the -5v to +5v that RS-232 uses. While possible, I doubt that your motherboard would have the I/O's for CMOS synchronous serial.

[Sparkfun]("https://www.sparkfun.com/") has a number of these to choose from ([like this one]("https://www.sparkfun.com/products/9067")) but they aren't VFD. Also, while their "protocol" is fairly simple I don't know if they're supported out of the box in Myth.

I would look for an RS-232 enabled display that meets your needs unless you can verify that your motherboard has the GPIO pins available and you can figure out how to access them.

---

### Post by milhouse on 2013-01-01
[Matrix Orbital]("http://www.matrixorbital.com/index.php") manufactures a ton of VFD LCDs with serial and USB interfaces. They are pricey, but since they are such a big player my guess is that they would be well supported and may just work out of the box once you configure the serial port address.

Check out page 14 from [this manual]("http://www.matrixorbital.ca/manuals/X-Board_Series/MOX%20%28Rev1.0%29.pdf") which shows the pinouts for the serial interface. You will want to make sure you get something that operates at RS-232 levels and not TTL (the linked display can do both). Also, Tx from your PC needs to connect to Rx on the display. But *sometimes* Rx and Tx on the device you are connecting to might not be labeled as you expect so you could end up with them backwards. No worries, just switch them if it doesn't work. Just make sure you get Vcc (power) and Gnd correct. Hooking those up incorrectly may not be o.k.!

It looks like Matrix Orbital provides cables for both power and data. Depending on your skills, you may choose to buy them to minimize the custom work, though you will most likely need to work up a custom end to the DB9 cable that mates to your motherboard header. Hopefully you have a connector that already fits that so you can cut the wires and splice into it. Your other option would be to go USB and use an internal USB header.

---

### Post by dc_wmj2 on 2013-01-01
Thanks for the replies. I posted in another forum already and didn't get usefull answers at all.

Synchronous Serial = CMOS Serial
SPI=?
RS232 = Usual Serial Port (= 9pin ?) = Asynchronous Serial ?

[This display]("http://noritake-vfd.com/ds1625m.aspx") has support for SPI and needs only 3 wires. Can I connect SPI to my
mainboard's serial-header?

The display I'm looking for must be a VFD and has a maximum size of 138 mm x 38 mm. Since this is really small
all crystalfontz-displays coming with a handy USB-connector are not possible. Same for most marix-orbital-displays. Possible sizes are usually 16x2 characters or 20x2. Something small and graphical would be awesome too of course. I found the company producing the original display. They are located in korea and ship it for 80 Euro! It seems there is no shop on the net selling it cheaper. Half the price is my upper budget-limit for a display, better 20 or 30 bucks.

The space for the display in the silverstone-case is very limited. The windows is covered by a black plastic-window, hence the need for VFD.

**Edit:** Just noticed I'm using two usernames here for some reason (whocares02=dc_wmj2). Second one is very old but still in my browser's auto-login. Sorry for confusion.

---

### Post by milhouse on 2013-01-01
SPI is a TTL level synchronous serial signaling interface commonly used for chip to chip communications. For example, a microcontroller could talk to a display or EEPROM using SPI. In TTL logic 0v is "low" and 5v is "high". CMOS Synchronous is similar, though I have no experience with it.

RS-232 signal levels can vary but a typical motherboard port operates at +12v for a high signal and -12v for a low signal. These levels are not compatible with TTL levels. There are IC's that convert between these levels (MAX232) and you could get your geek on by building a little circuit to interface a TTL level serial LCD to your PC but unless you're *really* hurting for something to do, I wouldn't bother.

You want either a USB interface or RS-232 serial. RS-232 serial is asynchronous, but don't worry about that.

---

### Post by whocares02 on 2013-01-02
This doesn't look good! All noritake-displays with RS232 are too big in size for me. That sucks!

**Edit: **Wait, [here]("http://noritake-vfd.com/gu144x16d-7053b.aspx") I found one. When searching for "asynchronous" the GU144X16D-7053B shows up. It supports serial-connection "Synchronous, Asynchronous, and SPI". One of the tables below the description reads (spacing of table doesn't work here):

> Pin assignment

 In the case of  Asynchronous-serial-interface

Pin No. 	Signal name 	Function 	Direction 
1     VCC    Power supply    Input 
2    SIN    Data Receive    Input 
3    GND    Ground    Input 
4    SBUSY    Display Busy    Output 
5    NC    Non connection    N/A
6    /RESET    Reset Display    Input
7    NC    Non connection    N/A

OK, now I get the same problem again: They show signal-names and -pin-assignments but I stil don't know how to connect them to serial-9-pin on the mainboard.

---

### Post by milhouse on 2013-01-02
That one will not work either. It too operates at TTL levels. Like I said, you need one that is either RS-232 or USB. Simply searching for "serial" interfaces isn't specific enough since it is the signal level that is the issue.

Check out [[COLOR="Sienna"]this[/COLOR]]("http://noritake-vfd.com/uart.aspx") page. These modules all come with a "backpack" board that provides an RS-232 interface. (there is a jumper that needs to be set so it works at RS-232 levels, not TTL).

---

### Post by whocares02 on 2013-01-02
This is just confusing. These UART-boards don't seem to support RS232. The GU144X16D-7053B I mentioned, is one of the UART-devices, supporting 3 different operation-modes. However, RS232 is not written anywhere on the details-page.

---

### Post by milhouse on 2013-01-02
Yeah, the text at the top of the page led me to believe that all of those units were available with an RS-232 interface. Clearly that is not the case. Some of them are, but not the one that seems to fit.

Just remember, you need an RS-232 or USB interface. Asynchronous serial still can be at TTL logic levels which will not work without level shifting.

Good luck!

---

