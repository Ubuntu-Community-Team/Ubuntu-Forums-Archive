---
title: "Gnome PPP will not connect even though Conexant HDA/HSF modem is installed"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by jre6 on 2010-05-30
I am a new Ubuntu user and run Ubuntu 9.04 (Jaunty Jackalope) on my laptop and desktop. I have a Conexant HSF modem on my desktop and Conexant HDA modem on my laptop. I installed the Conexant drivers according to the instructions given in the [URL="https://help.ubuntu.com/community/DialupModemHowto/Conexant"]
Conexant community wiki documentation[/URL]. I also installed Gnome PPP as the dialer. Gnome PPP dials out through the modem, but then it does not respond, just showing "Waiting for prompt" for about a minute and then returns to the connection details dialog box as given below. Please help.
[IMG]http://jonramvi.files.wordpress.com/2008/02/080220gnomeppp.png[/IMG]

---

### Post by pdc on 2010-05-30
what does

> lsusb

in a terminal give you for this device?

also 

> dmesg | grep tty

if you copy and paste back these

---

### Post by jre6 on 2010-05-31
Another problem occurs: the sound breaks even if I follow the instructions on the page.

I expect to paste lsusb and dmesg output after the sound is restored.

---

### Post by jre6 on 2010-06-04
After three days of hard work, I was able to restore the sound. I had to reinstall Ubuntu.

I have just described how I did it on my laptop which has the Conexant HDA modem.
I think the problem is with Gnome PPP, so if the problem on my laptop is resolved, the problem on my desktop would too beresolved in the same manner.

Here is how I installed the Conexant driver :

1)Installed alsa-driver-linuxant_1.0.20.3_all.deb
2)Installed the following packages:
            a)libxplc 0.3.13
            b)libwvstreams 4.4 base
            c)libwvstreams 4.4 extras
            d)libuniconf 4.4
            e)wvdial 1.60.1
     f)gnome-ppp 0.3.23
3)Installed the driver by the following method:
       a)Opened terminal:
       b)Typed the following:

```

rm -r hsfmodem-7.80.02.04full/modules/imported
cp -R hsfmodem-7.68.00.09oem/modules/imported hsfmodem-7.80.02.04full/modules/
cd hsfmodem-7.80.02.04full
gedit modules/imported/include/osservices.h

```3)Then on line 356 replaced #include <string.h> with #include <linux/string.h> and saved the file.
4)Then again typed the following into the terminal:

```

sudo make install
sudo /usr/sbin/hsfconfig

```This question had appeared. Just pressed enter:
Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.28-11-generic/build]
Modem was installed at ttySHSF0.

This was whatever the terminal returned:

```


ubuntu@ubuntu:~/hsfmodem-7.80.02.04full$ sudo make install
make[1]: Entering directory `/home/ubuntu/hsfmodem-7.80.02.04full/nvm'
mkdir -m 755 -p cvt
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2.inf | ./cvtinf.pl cvt/hsfpcibasic2; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic2 < "inf/hsf.cty"; else true; fi
(cd cvt/hsfpcibasic2/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2smart.inf | ./cvtinf.pl cvt/hsfpcibasic2smart; if [ -n "" ]; then ./cvtinf.pl cvt/hsfpcibasic2smart < ""; else true; fi
if [ -d cvt/hsfpcibasic2/Profile ]; then ln -sf ../hsfpcibasic2/Profile cvt/hsfpcibasic2smart/.; else true; fi
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic2smart/.
(cd cvt/hsfpcibasic2smart/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2smart/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2hsfi.inf | ./cvtinf.pl cvt/hsfpcibasic2hsfi; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic2hsfi < "inf/hsf.cty"; else true; fi
rm -rf cvt/hsfpcibasic2hsfi/Region
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic2hsfi/.
(cd cvt/hsfpcibasic2hsfi/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2hsfi/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2bry.inf | ./cvtinf.pl cvt/hsfpcibasic2bry; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic2bry < "inf/hsf.cty"; else true; fi
rm -rf cvt/hsfpcibasic2bry/Region
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic2bry/.
(cd cvt/hsfpcibasic2bry/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2bry/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic3.inf | ./cvtinf.pl cvt/hsfpcibasic3; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic3 < "inf/hsf.cty"; else true; fi
rm -rf cvt/hsfpcibasic3/Region
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic3/.
(cd cvt/hsfpcibasic3/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic3/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfmc97ich.inf | ./cvtinf.pl cvt/hsfmc97; if [ -n "" ]; then ./cvtinf.pl cvt/hsfmc97 < ""; else true; fi
rm -f mc97/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2smart/Profile cvt/hsfmc97/.
ln -sf ../hsfpcibasic2smart/Region cvt/hsfmc97/.
(cd cvt/hsfmc97/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfmc97/COUNTRY_CODE_LIST
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97ali
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97ati
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97ich
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97sis
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97via
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfcadmus2.inf | ./cvtinf.pl cvt/hsfcadmus2; if [ -n "" ]; then ./cvtinf.pl cvt/hsfcadmus2 < ""; else true; fi
rm -f cadmus2/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2/Profile cvt/hsfcadmus2/.
ln -sf ../hsfpcibasic2/Region cvt/hsfcadmus2/.
(cd cvt/hsfcadmus2/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfcadmus2/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfcadmus2smart.inf | ./cvtinf.pl cvt/hsfcadmus2smart; if [ -n "" ]; then ./cvtinf.pl cvt/hsfcadmus2smart < ""; else true; fi
rm -f cadmus2smart/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2smart/Profile cvt/hsfcadmus2smart/.
ln -sf ../hsfpcibasic2smart/Region cvt/hsfcadmus2smart/.
(cd cvt/hsfcadmus2smart/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfcadmus2smart/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfhda.inf | ./cvtinf.pl cvt/hsfhda; if [ -n "" ]; then ./cvtinf.pl cvt/hsfhda < ""; else true; fi
rm -f hda/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2smart/Profile cvt/hsfhda/.
ln -sf ../hsfpcibasic2smart/Region cvt/hsfhda/.
(cd cvt/hsfhda/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfhda/COUNTRY_CODE_LIST
cd cvt && find . -type f ! -empty -exec md5sum {} ';' | sort | \
    while read sum file ; do \
        if [ "$sum" = "$prevsum" ] && cmp -s "$file" "$prevfile"; then \
            rm -f "$file"; \
            if ! ln "$prevfile" "$file"; then \
                echo 2>&1 "$0: ln FAILED - recreate $file based on $prevfile"; \
                exit 1; \
            fi; \
        else \
            prevsum="$sum"; \
            prevfile="$file"; \
        fi; \
    done
touch cvt/.linksame
mkdir -m 755 -p /etc/hsfmodem/nvm
cd cvt && (find  hsfpcibasic2  hsfpcibasic2smart  hsfpcibasic2hsfi  hsfpcibasic2bry  hsfpcibasic3  hsfmc97  hsfmc97ali  hsfmc97ati  hsfmc97ich  hsfmc97sis  hsfmc97via  hsfcadmus2  hsfcadmus2smart  hsfhda | cpio -pdmu /etc/hsfmodem/nvm)
127 blocks
make[1]: Leaving directory `/home/ubuntu/hsfmodem-7.80.02.04full/nvm'
make[1]: Entering directory `/home/ubuntu/hsfmodem-7.80.02.04full/scripts'
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!i386!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < patcher.in > patcher
chmod --reference=patcher.in patcher
ln -s cnxtconfig.in hsfconfig.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!i386!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfconfig.in > hsfconfig
chmod --reference=hsfconfig.in hsfconfig
ln -s cnxtstop.in hsfstop.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!i386!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfstop.in > hsfstop
chmod --reference=hsfstop.in hsfstop
ln -s cnxtmodconflicts.in hsfmodconflicts.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!i386!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfmodconflicts.in > hsfmodconflicts
chmod --reference=hsfmodconflicts.in hsfmodconflicts
ln -s cnxtdcpd.in hsfdcpd.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!i386!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfdcpd.in > hsfdcpd
chmod --reference=hsfdcpd.in hsfdcpd
install -m 700 hsfconfig hsfstop hsfmodconflicts hsfdcpd /usr/sbin
ln -s rccnxt.in rchsf.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!i386!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < rchsf.in > rchsf
chmod --reference=rchsf.in rchsf
mkdir -m 755 -p /usr/lib/hsfmodem
install -m 700 rchsf /usr/lib/hsfmodem
make[1]: Leaving directory `/home/ubuntu/hsfmodem-7.80.02.04full/scripts'
make[1]: Entering directory `/home/ubuntu/hsfmodem-7.80.02.04full/modules'
rm -rf "/usr/lib/hsfmodem/config.mak" "/usr/lib/hsfmodem/modules/imported" "/usr/lib/hsfmodem/modules"
mkdir -m 755 -p /usr/lib/hsfmodem/modules
(cd .. && find config.mak modules/imported -depth -print | cpio -pdmu /usr/lib/hsfmodem)
5857 blocks
find . \( -name COPYING -o -name '*.sh' -o -name '*.[ch]' -o -name '*.mak' -o -name '[Mm]akefile' \) -print | cpio -pdmu /usr/lib/hsfmodem/modules
3706 blocks
find binaries -depth -print | cpio -pdmu /usr/lib/hsfmodem/modules
0 blocks
make[1]: Leaving directory `/home/ubuntu/hsfmodem-7.80.02.04full/modules'
make[1]: Entering directory `/home/ubuntu/hsfmodem-7.80.02.04full/diag'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/ubuntu/hsfmodem-7.80.02.04full/diag'
mkdir -p /etc/hsfmodem/log
install -m 444 LICENSE /usr/lib/hsfmodem

To complete the installation and configuration of your modem,
please run "hsfconfig" (or "/usr/sbin/hsfconfig")
ubuntu@ubuntu:~/hsfmodem-7.80.02.04full$ sudo /usr/sbin/hsfconfig
Conexant HSF softmodem driver, version 7.68.00.09oem

If you need assistance or more information, please go to:
    http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Ubuntu-9.04 linux-2.6.28-11-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.28-11-generic/build] 

Building modules for kernel 2.6.28-11-generic, using source directory
/lib/modules/2.6.28-11-generic/build. Please wait...
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_conexant is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_conexant,snd_hda_codec_idt,snd_hda_intel
Sending TERM signal to processes still using the driver:
  PID USER     COMMAND
16197 ubuntu   /usr/bin/pulseaudio --start --log-target=syslog
Successfully stopped the Conexant HSF softmodem driver.
done.

Unable to determine region, defaulting to "USA"

Please enter region name for modem unit 0 [USA]: 

Setting region for modem unit 0: "USA"

To change, use "hsfconfig --region" or "AT+GCI=<T35code>"
The current region can be displayed by entering "ATI9" in a terminal program.

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati

Current parameters: ("hsfconfig --info")

Config for modem unit 0: /dev/ttySHSF0
    Device instance: 0-HDA-14f12bfa:14f100c3-1
    HW revision    : SSD=31 LSD=0x11
    HW profile name: hsfhda
    Current region : USA (T.35 code: 00B5)

The /dev/modem alias (symlink) points to ttySHSF0
ubuntu@ubuntu:~/hsfmodem-7.80.02.04full$ 

```Now, I dialed using Gnome-PPP. The connection failed. Here is some report from the log:

```

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT172222
--> Waiting for carrier.
ATM1L3DT172222
CONNECT 115200 
--> Carrier detected.  Waiting for prompt.
Welcome to UTStarcom Total Control HiPer ARC (TM)
Networks That Go The Distance (TM)
login: 
--> Looks like a login prompt.
--> Sending: 23592876
23592876
Password: 
--> Looks like a password prompt.
--> Sending: (password)
~[7f]}#@!}!}!} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} [12]J~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}"} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} [07]+~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}#} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} t[0b]~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}$} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} -i~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}%} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} ^I~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}&} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} K(~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}'} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} 8}(~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}(} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} he~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!})} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} };E~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}*} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&\[17][(}'}"}(}"}1}$}%j}3}#} }.$~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT172222
--> Waiting for carrier.
NO CARRIER
ATM1L3DT172222
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Fri Jun  4 15:04:26 2010

```Typing dmesg in terminal gives this. Couldn't copy the whole message as the display limit of the terminal exceeded:

```

[    0.456044] Total of 2 processors activated (7979.97 BogoMIPS).
[    0.456100] CPU0 attaching sched-domain:
[    0.456103]  domain 0: span 0-1 level MC
[    0.456105]   groups: 0 1
[    0.456111] CPU1 attaching sched-domain:
[    0.456113]  domain 0: span 0-1 level MC
[    0.456115]   groups: 1 0
[    0.456187] net_namespace: 776 bytes
[    0.456187] Booting paravirtualized kernel on bare hardware
[    0.456325] Time: 14:30:13  Date: 06/04/10
[    0.456325] regulator: core version 0.5
[    0.456325] NET: Registered protocol family 16
[    0.456325] EISA bus registered
[    0.456325] ACPI: bus type pci registered
[    0.456325] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.456325] PCI: MCFG area at f0000000 reserved in E820
[    0.456325] PCI: Using MMCONFIG for extended config space
[    0.456325] PCI: Using configuration type 1 for base access
[    0.457150] ACPI: EC: Look up EC in DSDT
[    0.488393] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] - 00, should be A9 [20080926]
[    0.488400] ACPI: SSDT 3F6819CE, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    0.498657] ACPI: Interpreter enabled
[    0.498662] ACPI: (supports S0 S3 S4 S5)
[    0.498670] ACPI: Using IOAPIC for interrupt routing
[    0.558764] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.558777] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.558866] pci 0000:00:02.0: reg 10 32bit mmio: [0xeff00000-0xeff7ffff]
[    0.558871] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
[    0.558876] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.558881] pci 0000:00:02.0: reg 1c 32bit mmio: [0xefec0000-0xefefffff]
[    0.558916] pci 0000:00:02.1: reg 10 32bit mmio: [0xeff80000-0xefffffff]
[    0.559033] pci 0000:00:1b.0: reg 10 64bit mmio: [0xefebc000-0xefebffff]
[    0.559074] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.559079] pci 0000:00:1b.0: PME# disabled
[    0.559147] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.559152] pci 0000:00:1c.0: PME# disabled
[    0.559223] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.559228] pci 0000:00:1c.2: PME# disabled
[    0.559294] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.559358] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.559423] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.559486] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.559553] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80000-0xffa803ff]
[    0.559600] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.559605] pci 0000:00:1d.7: PME# disabled
[    0.559766] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.559771] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.559822] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.559830] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.559838] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.559847] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.559855] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.559880] pci 0000:00:1f.2: PME# supported from D3hot
[    0.559884] pci 0000:00:1f.2: PME# disabled
[    0.559947] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.560168] pci 0000:09:00.0: reg 10 64bit mmio: [0xefdf0000-0xefdfffff]
[    0.560226] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.560232] pci 0000:09:00.0: PME# disabled
[    0.560302] pci 0000:00:1c.2: bridge 32bit mmio: [0xefd00000-0xefdfffff]
[    0.560360] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.560374] pci 0000:03:01.0: supports D1 D2
[    0.560376] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.560381] pci 0000:03:01.0: PME# disabled
[    0.560447] pci 0000:00:1e.0: transparent bridge
[    0.560503] bus 00 -> node 0
[    0.560509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.560910] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.561057] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.561186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    0.572255] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.572386] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.572516] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.572629] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.572760] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.572890] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.573024] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.573157] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.573308] ACPI: WMI: Mapper loaded
[    0.573346] SCSI subsystem initialized
[    0.573346] libata version 3.00 loaded.
[    0.573346] usbcore: registered new interface driver usbfs
[    0.573346] usbcore: registered new interface driver hub
[    0.573346] usbcore: registered new device driver usb
[    0.573346] PCI: Using ACPI for IRQ routing
[    0.580010] Bluetooth: Core ver 2.13
[    0.580024] NET: Registered protocol family 31
[    0.580024] Bluetooth: HCI device and connection manager initialized
[    0.580024] Bluetooth: HCI socket layer initialized
[    0.580024] NET: Registered protocol family 8
[    0.580024] NET: Registered protocol family 20
[    0.580036] NetLabel: Initializing
[    0.580037] NetLabel:  domain hash size = 128
[    0.580039] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.580053] NetLabel:  unlabeled traffic allowed by default
[    0.580068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.580073] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.584058] AppArmor: AppArmor Filesystem Enabled
[    0.588015] Switched to high resolution mode on CPU 0
[    0.588715] Switched to high resolution mode on CPU 1
[    0.592017] pnp: PnP ACPI init
[    0.592025] ACPI: bus type pnp registered
[    0.623853] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.623856] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.623938] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.623941] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.623944] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.623947] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649372] pnp: PnP ACPI: found 14 devices
[    0.649375] ACPI: ACPI bus type pnp unregistered
[    0.649378] PnPBIOS: Disabled by ACPI PNP
[    0.649387] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.649390] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.649393] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.649396] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.649398] system 00:00: iomem range 0x100000-0x3f6813ff could not be reserved
[    0.649401] system 00:00: iomem range 0x3f681400-0x3f6fffff has been reserved
[    0.649403] system 00:00: iomem range 0x3f700000-0x3f7fffff has been reserved
[    0.649406] system 00:00: iomem range 0x3f700000-0x3fefffff could not be reserved
[    0.649409] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.649411] system 00:00: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.649414] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.649416] system 00:00: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.649419] system 00:00: iomem range 0xfed45000-0xfed9ffff has been reserved
[    0.649422] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.649424] system 00:00: iomem range 0xf4000000-0xf4003fff has been reserved
[    0.649427] system 00:00: iomem range 0xf4004000-0xf4004fff has been reserved
[    0.649429] system 00:00: iomem range 0xf4005000-0xf4005fff has been reserved
[    0.649432] system 00:00: iomem range 0xf4006000-0xf4006fff has been reserved
[    0.649435] system 00:00: iomem range 0xf4008000-0xf400bfff has been reserved
[    0.649437] system 00:00: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.649444] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.649450] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.649452] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.649455] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.649457] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.649465] system 00:08: ioport range 0xc80-0xcaf has been reserved
[    0.649467] system 00:08: ioport range 0xcc0-0xcff could not be reserved
[    0.649470] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.649472] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.649474] system 00:08: ioport range 0xcbc-0xcbf has been reserved
[    0.649477] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.649484] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.649490] system 00:0d: ioport range 0xcb0-0xcbb has been reserved
[    0.649493] system 00:0d: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.684207] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.684209] pci 0000:00:1c.0:   IO window: disabled
[    0.684216] pci 0000:00:1c.0:   MEM window: disabled
[    0.684220] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.684228] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:09
[    0.684230] pci 0000:00:1c.2:   IO window: disabled
[    0.684236] pci 0000:00:1c.2:   MEM window: 0xefd00000-0xefdfffff
[    0.684241] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.684255] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.684257] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.684262] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.684268] pci 0000:03:01.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.684274] pci 0000:03:01.0:   MEM window: 0x54000000-0x57ffffff
[    0.684279] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.684282] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.684289] pci 0000:00:1e.0:   MEM window: 0x54000000-0x59ffffff
[    0.684294] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.684311] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.684318] pci 0000:00:1c.0: setting latency timer to 64
[    0.684328] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.684333] pci 0000:00:1c.2: setting latency timer to 64
[    0.684341] pci 0000:00:1e.0: setting latency timer to 64
[    0.684351] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.684355] pci 0000:03:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.684364] bus: 00 index 0 io port: [0x00-0xffff]
[    0.684366] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.684368] bus: 0b index 0 mmio: [0x0-0x0]
[    0.684370] bus: 0b index 1 mmio: [0x0-0x0]
[    0.684371] bus: 0b index 2 mmio: [0x0-0x0]
[    0.684374] bus: 0b index 3 mmio: [0x0-0x0]
[    0.684376] bus: 09 index 0 mmio: [0x0-0x0]
[    0.684378] bus: 09 index 1 mmio: [0xefd00000-0xefdfffff]
[    0.684380] bus: 09 index 2 mmio: [0x0-0x0]
[    0.684381] bus: 09 index 3 mmio: [0x0-0x0]
[    0.684383] bus: 03 index 0 io port: [0x2000-0x2fff]
[    0.684385] bus: 03 index 1 mmio: [0x54000000-0x59ffffff]
[    0.684387] bus: 03 index 2 mmio: [0x50000000-0x53ffffff]
[    0.684389] bus: 03 index 3 io port: [0x00-0xffff]
[    0.684391] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.684393] bus: 04 index 0 io port: [0x2000-0x20ff]
[    0.684395] bus: 04 index 1 io port: [0x2400-0x24ff]
[    0.684397] bus: 04 index 2 mmio: [0x50000000-0x53ffffff]
[    0.684399] bus: 04 index 3 mmio: [0x54000000-0x57ffffff]
[    0.684407] NET: Registered protocol family 2
[    0.696056] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.696289] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.696628] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.696800] TCP: Hash tables configured (established 131072 bind 65536)
[    0.696802] TCP reno registered
[    0.700069] NET: Registered protocol family 1
[    0.700178] checking if image is initramfs... it is
[    1.001011] Clocksource tsc unstable (delta = 2130317352 ns)
[    1.321125] Freeing initrd memory: 7566k freed
[    1.321344] cpufreq: No nForce2 chipset.
[    1.321495] audit: initializing netlink socket (disabled)
[    1.321524] type=2000 audit(1275661813.320:1): initialized
[    1.328634] highmem bounce pool size: 64 pages
[    1.328639] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.329985] VFS: Disk quotas dquot_6.5.1
[    1.330046] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.330653] fuse init (API version 7.10)
[    1.330733] msgmni has been set to 1724
[    1.330945] alg: No test for stdrng (krng)
[    1.330959] io scheduler noop registered
[    1.330961] io scheduler anticipatory registered
[    1.330963] io scheduler deadline registered
[    1.330976] io scheduler cfq registered (default)
[    1.330988] pci 0000:00:02.0: Boot video device
[    1.368802] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.368853] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.368891] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.368908] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.368921] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.368933] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.369017] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.369066] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.369100] pcieport-driver 0000:00:1c.2: irq 2302 for MSI/MSI-X
[    1.369115] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.369128] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.369140] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.369222] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.369280] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.369810] ACPI: AC Adapter [AC] (on-line)
[    1.397520] ACPI: Battery Slot [BAT0] (battery present)
[    1.397567] ACPI: Battery Slot [BAT1] (battery absent)
[    1.397641] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.398224] ACPI: Lid Switch [LID]
[    1.398271] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.398277] ACPI: Power Button (CM) [PBTN]
[    1.398317] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.398320] ACPI: Sleep Button (CM) [SBTN]
[    1.398866] ACPI: SSDT 3F682138, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.399189] ACPI: SSDT 3F681EED, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.399534] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.399559] processor ACPI_CPU:00: registered as cooling_device0
[    1.399563] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.399901] ACPI: SSDT 3F68237C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.400217] ACPI: SSDT 3F6820B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.400581] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.400600] processor ACPI_CPU:01: registered as cooling_device1
[    1.400605] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.424777] thermal LNXTHERM:01: registered as thermal_zone0
[    1.428048] ACPI: Thermal Zone [THM] (62 C)
[    1.428106] isapnp: Scanning for PnP cards...
[    1.782851] isapnp: No Plug & Play device found
[    1.789184] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.789308] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.789818] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.790525] brd: module loaded
[    1.790827] loop: module loaded
[    1.790893] Fixed MDIO Bus: probed
[    1.790900] PPP generic driver version 2.4.2
[    1.790955] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.790984] Driver 'sd' needs updating - please use bus_type methods
[    1.790993] Driver 'sr' needs updating - please use bus_type methods
[    1.791060] ata_piix 0000:00:1f.2: version 2.12
[    1.791077] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.791081] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.791123] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.791220] scsi0 : ata_piix
[    1.791320] scsi1 : ata_piix
[    1.793195] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.793197] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.956477] ata1.00: ATA-7: TOSHIBA MK8037GSX, DL240D, max UDMA/100
[    1.956479] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.964490] ata1.00: configured for UDMA/100
[    2.128495] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A103, max UDMA/33
[    2.144455] ata2.00: configured for UDMA/33
[    2.147203] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8037GS DL24 PQ: 0 ANSI: 5
[    2.147298] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.147314] sd 0:0:0:0: [sda] Write Protect is off
[    2.147316] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.147342] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.147401] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.147416] sd 0:0:0:0: [sda] Write Protect is off
[    2.147418] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.147442] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.147445]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    2.577418] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.577457] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.581379] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5
[    2.585398] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.585401] Uniform CD-ROM driver Revision: 3.20
[    2.585482] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.585519] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.586124] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.586145] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.586166] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.586171] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.586236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.590160] ehci_hcd 0000:00:1d.7: debug port 1
[    2.590167] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.590180] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    2.604018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.604095] usb usb1: configuration #1 chosen from 1 choice
[    2.604122] hub 1-0:1.0: USB hub found
[    2.604129] hub 1-0:1.0: 8 ports detected
[    2.604248] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.604262] uhci_hcd: USB Universal Host Controller Interface driver
[    2.604281] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.604288] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.604291] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.604331] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.604358] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    2.604432] usb usb2: configuration #1 chosen from 1 choice
[    2.604456] hub 2-0:1.0: USB hub found
[    2.604465] hub 2-0:1.0: 2 ports detected
[    2.604547] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.604553] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.604557] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.604599] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.604634] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    2.604704] usb usb3: configuration #1 chosen from 1 choice
[    2.604728] hub 3-0:1.0: USB hub found
[    2.604735] hub 3-0:1.0: 2 ports detected
[    2.604819] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.604825] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.604829] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.604868] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.604901] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    2.604973] usb usb4: configuration #1 chosen from 1 choice
[    2.605000] hub 4-0:1.0: USB hub found
[    2.605008] hub 4-0:1.0: 2 ports detected
[    2.605090] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.605096] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.605099] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.605146] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.605181] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    2.605253] usb usb5: configuration #1 chosen from 1 choice
[    2.605277] hub 5-0:1.0: USB hub found
[    2.605283] hub 5-0:1.0: 2 ports detected
[    2.605405] usbcore: registered new interface driver libusual
[    2.605433] usbcore: registered new interface driver usbserial
[    2.605446] USB Serial support registered for generic
[    2.605465] usbcore: registered new interface driver usbserial_generic
[    2.605466] usbserial: USB Serial Driver core
[    2.605522] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.608591] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.608596] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.612046] mice: PS/2 mouse device common for all mice
[    2.628081] rtc_cmos 00:06: RTC can wake from S4
[    2.628111] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.628143] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.628200] device-mapper: uevent: version 1.0.3
[    2.628292] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.628401] device-mapper: multipath: version 1.0.5 loaded
[    2.628404] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.628483] EISA: Probing bus 0 at eisa.0
[    2.628485] EISA: Cannot allocate resource for mainboard
[    2.628488] Cannot allocate resource for EISA slot 1
[    2.628490] Cannot allocate resource for EISA slot 2
[    2.628515] EISA: Detected 0 cards.
[    2.628643] cpuidle: using governor ladder
[    2.628762] cpuidle: using governor menu
[    2.629245] TCP cubic registered
[    2.629338] NET: Registered protocol family 10
[    2.629757] lo: Disabled Privacy Extensions
[    2.630082] NET: Registered protocol family 17
[    2.630099] Bluetooth: L2CAP ver 2.11
[    2.630101] Bluetooth: L2CAP socket layer initialized
[    2.630103] Bluetooth: SCO (Voice Link) ver 0.6
[    2.630105] Bluetooth: SCO socket layer initialized
[    2.630156] Bluetooth: RFCOMM socket layer initialized
[    2.630161] Bluetooth: RFCOMM TTY layer initialized
[    2.630163] Bluetooth: RFCOMM ver 1.10
[    2.630628] Using IPI No-Shortcut mode
[    2.630694] registered taskstats version 1
[    2.630778]   Magic number: 14:261:535
[    2.630785] bdi 1:13: hash matches
[    2.630864] rtc_cmos 00:06: setting system clock to 2010-06-04 14:30:15 UTC (1275661815)
[    2.630868] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.630869] EDD information not available.
[    2.631132] Freeing unused kernel memory: 532k freed
[    2.631281] Write protecting the kernel text: 4128k
[    2.631338] Write protecting the kernel read-only data: 1532k
[    2.631603] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.878156] tg3.c:v3.94 (August 14, 2008)
[    2.878227] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.878242] tg3 0000:09:00.0: setting latency timer to 64
[    2.902162] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:18:8b:d5:b8:6e
[    2.902166] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    2.902168] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.212058] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.360502] usb 2-2: configuration #1 chosen from 1 choice
[    3.362453] hub 2-2:1.0: USB hub found
[    3.364427] hub 2-2:1.0: 4 ports detected
[    3.608059] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    3.682861] ISO 9660 Extensions: Microsoft Joliet Level 3
[    3.723819] ISO 9660 Extensions: RRIP_1991A
[    3.780041] usb 4-2: configuration #1 chosen from 1 choice
[    3.787478] usbcore: registered new interface driver hiddev
[    3.804241] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5
[    3.808083] generic-usb 0003:413C:3016.0001: input,hidraw0: USB HID v1.11 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    3.808098] usbcore: registered new interface driver usbhid
[    3.808101] usbhid: v2.6:USB HID core driver
[    3.857426] usb 2-2.3: new full speed USB device using uhci_hcd and address 3
[    3.985476] usb 2-2.3: configuration #1 chosen from 1 choice
[    3.987448] hub 2-2.3:1.0: USB hub found
[    3.989422] hub 2-2.3:1.0: 3 ports detected
[    4.070775] aufs 20080922
[    4.269424] usb 2-2.3.2: new full speed USB device using uhci_hcd and address 4
[    4.355992] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[    4.387486] usb 2-2.3.2: configuration #1 chosen from 1 choice
[   69.504369] udev: starting version 141
[   71.855871] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   71.925634] Linux agpgart interface v0.103
[   71.989487] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   72.043821] intel_rng: FWH not detected
[   72.104727] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:28/input/input7
[   72.112118] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   72.112189] ACPI Warning (nspredef-0357): \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) [20080926]
[   72.112295] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/input/input8
[   72.117093] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   72.344151] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   72.345281] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   72.348624] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   72.352659] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01c2]
[   72.352686] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[   72.352687] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
[   72.404544] iTCO_vendor_support: vendor-support=0
[   72.475963] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   72.476082] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   72.476150] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   72.481517] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 18
[   72.481521] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   72.481525] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   72.481532] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   72.481535] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   72.481761] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x54000000 - 0x59ffffff
[   72.481763] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   72.586560] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   72.700108] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   72.700174] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   72.910483] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   72.912481] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   72.913312] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   72.913999] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   72.914688] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   73.488154] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   73.512545] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   85.986828] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   85.986831] Bluetooth: BNEP filters: protocol multicast
[   86.015629] Bridge firewalling registered
[   92.568058] lp: driver loaded but no devices found
[   92.620118] ppdev: user-space parallel port driver
[   94.581684] [drm] Initialized drm 1.1.0 20060810
[   94.683882] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   94.683887] pci 0000:00:02.0: setting latency timer to 64
[   94.684038] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   94.685581] [drm:i915_setparam] *ERROR* unknown parameter 4
[   94.685604] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   95.131538] tg3 0000:09:00.0: irq 2301 for MSI/MSI-X
[   95.215321] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   96.609675] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  119.943164] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  206.828122] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  206.962878] usb 1-5: configuration #1 chosen from 1 choice
[  210.569453] Initializing USB Mass Storage driver...
[  210.570027] scsi2 : SCSI emulation for USB Mass Storage devices
[  210.571522] usbcore: registered new interface driver usb-storage
[  210.571529] USB Mass Storage support registered.
[  210.571712] usb-storage: device found at 4
[  210.571716] usb-storage: waiting for device to settle before scanning
[  215.568334] usb-storage: device scan complete
[  215.569126] scsi 2:0:0:0: Direct-Access     JetFlash TS4GJFV60        8.07 PQ: 0 ANSI: 2
[  215.572798] sd 2:0:0:0: [sdb] 7852032 512-byte hardware sectors: (4.02 GB/3.74 GiB)
[  215.586270] sd 2:0:0:0: [sdb] Write Protect is off
[  215.586277] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  215.586282] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  215.588197] sd 2:0:0:0: [sdb] 7852032 512-byte hardware sectors: (4.02 GB/3.74 GiB)
[  215.588691] sd 2:0:0:0: [sdb] Write Protect is off
[  215.588696] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  215.588700] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  215.588707]  sdb: sdb1
[  215.863406] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  215.863540] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  560.608613] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  581.002268] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  581.002384] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  581.112361] patch_cxthsfmodem: Conexant HSF modem detected but driver not present
[  581.120512] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input11
[  581.125394] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input12
[  685.493026] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1813.084101] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1818.057566] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[ 1818.173733] usbcore: registered new interface driver hsfusbcd2
[ 1818.204011] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 1818.204621] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1818.851108] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12bfa:14f100c3-1)
[ 1818.852553] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[ 1818.866262] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input14
[ 1820.747506] usbcore: deregistering interface driver hsfusbcd2
[ 1820.835430] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1822.173700] usbcore: registered new interface driver hsfusbcd2
[ 1822.204096] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 1822.204387] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1822.832393] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12bfa:14f100c3-1)
[ 1822.832801] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input15
[ 1822.840304] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input16
[ 1826.066840] usbcore: deregistering interface driver hsfusbcd2
[ 1826.148475] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1827.520910] usbcore: registered new interface driver hsfusbcd2
[ 1827.552198] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 1827.552414] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1828.186379] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12bfa:14f100c3-1)
[ 1828.186773] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input17
[ 1828.196600] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input18

```And typing lsusb in terminal gives this:

```

Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

