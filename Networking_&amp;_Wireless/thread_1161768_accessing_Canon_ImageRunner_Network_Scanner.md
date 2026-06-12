---
title: "accessing Canon ImageRunner Network Scanner"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by balud66 on 2009-05-17
Is there any way to use this device in ubuntu? (Canon IR 2018, Printer, Scanner, Fax etc.)

or do I have to go back to Microsoft Windows?

Seems that Linux is not really usable when into serious business, still just for computer geeks?

:(

(btw, this is a *real* network scanner, printer, *not* just a printer/scanner connected to a computer via usb etc.)

---

### Post by chili555 on 2009-05-17
Well, the printing part should be fairly straightforward. Open System -> Administration -> Printing and select New -> Printer. The system will search for printers and, most likely, the printer will be detected and added automagically. If not, I suggest selecting IPP printer, add the details, including the IP address of the printer. You should end up with, approximately:```
ipp://192.168.whatever:631/printers/Canon2018
```The drivers for your printer are already built in.> Seems that Linux is not really usable when into serious business, still just for computer geeks?Not really. It just depends on whether you are willing to do a bit of extra work in order to live in the open source world, blissfully free of virii, malware, spyware and all those $300 colorful cardboard boxes that contain nothing but a CD and an incomprehensible manual. Oh, and you'll need to purchase the upgrade if you want it to work with Windows 7. 

As for the scanner and fax, I am hoping others will jump in here.

---

### Post by douceka on 2009-11-01
I think it might be more complicated in Ubuntu 9.04 and 9.10.
I suggest to do this:

Use sript tisk.sh and go to (6.) or do it yourself:


1. Download necesary packages

```
mkdir ~/canon_printer/

cd ~/canon_printer/

wget -c http://ftp.cz.debian.org/debian/pool/main/l/lzo/liblzo1_1.08-3_i386.deb http://ftp.cz.debian.org/debian/pool/main/o/opencdk8/libopencdk8_0.5.9-2_i386.deb http://ftp.cz.debian.org/debian/pool/main/g/gnutls13/libgnutls13_1.4.4-3+etch4_i386.deb  http://files.canon-europe.com/files/soft31040/software/g8b5enx.zip 
```2. Install it

```
sudo dpkg -i liblzo1_1.08-3_i386.deb libopencdk8_0.5.9-2_i386.deb libgnutls13_1.4.4-3+etch4_i386.deb 

unzip g8b5enx -d g8b5enx

```3. Make your own "cndrvcups-common"  !OR! download my here and go to (4.)

3.1 Install packages for make

```
sudo apt-get install  build-essential    gettext    automake        debhelper     libglib2.0-dev   libcups2 libtool libgtk2.0-dev

```3.2. Prepare and configure it

```
cd g8b5enx/UK/Sources/

tar xvf cndrvcups-common-1.80-1.tar.gz

cd cndrvcups-common-1.80

sed debian/control --in-place -e 's/Depends: ${shlibs:Depends}, ${misc:Depends}, cupsys, gs-esp, libcupsys2 (>= 1.1.23)/Depends: ${shlibs:Depends}, ${misc:Depends}, cupsys, gs-esp, libcups2/g' 
```3.3 Make package

```
dpkg-buildpackage

```3.4 Install it

```
sudo dpkg -i cndrvcups-common_1.80-1_i386.deb
cd ../../

```4. install cndrvcups-ufr2-uk_1.80-1_i386.deb

```
sudo dpkg -i 32-bit_Driver/Debian/cndrvcups-ufr2-uk_1.80-1_i386.deb
```5. Restart CUPS

```
sudo /etc/init.d/cups restart
```6. Add your printer

6.1 Go to Admnistration > Printer > New > Printer > other&#8230;,  give uri (i.e. lpd://192.168.xxx.yyy/PASSTHRU, more info [http://saysprasad.wordpress.com/2009/03/31/how-to-configure-canon-ir2018n-as-a-network-printer-in-linux/](http://saysprasad.wordpress.com/2009/03/31/how-to-configure-canon-ir2018n-as-a-network-printer-in-linux/)) of the printer in the right column. Click &#8216;Forward&#8217;

6.2 In the next menu select appropriate model. Click forward, give the Name as you would like to see. 
Important: must be something like "Canon iR2018 UFRII LT ver.1.8" !!!

7. Thats all, you have sucessfully installed a network printer.


tisk.sh:

```

#douceka @ http://ubuntuforums.org

mkdir ~/canon_printer/

cd ~/canon_printer/

wget -c http://ftp.cz.debian.org/debian/pool/main/l/lzo/liblzo1_1.08-3_i386.deb http://ftp.cz.debian.org/debian/pool/main/o/opencdk8/libopencdk8_0.5.9-2_i386.deb http://ftp.cz.debian.org/debian/pool/main/g/gnutls13/libgnutls13_1.4.4-3+etch4_i386.deb  http://files.canon-europe.com/files/soft31040/software/g8b5enx.zip 

sudo dpkg -i liblzo1_1.08-3_i386.deb libopencdk8_0.5.9-2_i386.deb libgnutls13_1.4.4-3+etch4_i386.deb 

sudo apt-get install  build-essential    gettext    automake        debhelper     libglib2.0-dev   libcups2 libtool libgtk2.0-dev

unzip g8b5enx -d g8b5enx

cd g8b5enx/UK/Sources

tar xvf cndrvcups-common-1.80-1.tar.gz

cd cndrvcups-common-1.80

sed debian/control --in-place -e 's/Depends: ${shlibs:Depends}, ${misc:Depends}, cupsys, gs-esp, libcupsys2 (>= 1.1.23)/Depends: ${shlibs:Depends}, ${misc:Depends}, cupsys, gs-esp, libcups2/g' 

dpkg-buildpackage

cd ../

sudo dpkg -i cndrvcups-common_1.80-1_i386.deb

sudo dpkg -i ../32-bit_Driver/Debian/cndrvcups-ufr2-uk_1.80-1_i386.deb

sudo /etc/init.d/cups restart


```

---

### Post by Caglar Yuksel on 2009-11-05
> **balud66 said:**
> Is there any way to use this device in ubuntu? (Canon IR 2018, Printer, Scanner, Fax etc.)

or do I have to go back to Microsoft Windows?

Seems that Linux is not really usable when into serious business, still just for computer geeks?

:(

(btw, this is a *real* network scanner, printer, *not* just a printer/scanner connected to a computer via usb etc.)

Yes, there is a way to overcome this problem that I recently achieved. You will see, it is a really easy way.

One of a iR2018 is available in my office that had no problem with 9.04. After upgrading it from 9.04 to 9.10, installing driver pack of canon became impossible. Then I have re-installed 9.04 and worked on it.

Solution:
1. open the web page [http://mirror.ne.gov/ubuntu/pool/universe/c/cups/ ]("http://mirror.ne.gov/ubuntu/pool/universe/c/cups/")
2. download the [libcupsys2_1.3.9-17ubuntu3.2_all.deb]("http://mirror.ne.gov/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.2_all.deb") and install it.
3. now you can install driver pack.

For Canon iR2018:
[http://software.canon-europe.com/software/0031040.asp?model=](http://software.canon-europe.com/software/0031040.asp?model=)
(follow the instructions of readme file in the package for installing)

---

