---
title: "Alsamixer not working"
date: 2011-07-25
forum: Multimedia Software
---

### Post by Number1luda on 2011-07-25
Right, I had some problems with my sound, tried updating some stuff, but looks like I only managed to screw it up even more.

Here is my problem atm


```
$ alsamixer
cannot open mixer: No such file or directory

```

I tried searching everywhere, but not solid answers to my specific problem, or anything I tried work.


Any ideas?

---

### Post by .... on 2011-07-25
>  tried updating some stuff
Be more specific. It's difficult to help you undo something if we don't know what you did.

---

### Post by tjones00 on 2011-07-25
```
sudo find / -name alsamixer
```

should return 
```

/usr/bin/alsamixer
```

If not

```
sudo apt-get install alsa-utils
```

---

### Post by Number1luda on 2011-07-26
> **.... said:**
> Be more specific. It's difficult to help you undo something if we don't know what you did.

tried to update alsamixer since I didnt have the last version and I was having some issues with sound.

```

sudo find / -name alsamixer

```

returns

```

/usr/src/alsa/alsa-utils-1.0.24.2/alsamixer
/usr/src/alsa/alsa-utils-1.0.24.2/alsamixer/alsamixer
/usr/bin/alsamixer
/home/.../Downloads/alsa-utils-1.0.24.2/alsamixer




```

---

### Post by tjones00 on 2011-07-26
Ok you've established that alsamixer is installed and in the proper location.

/usr/bin/alsamixer

Try 
```

sudo alsamixer

```If that works it means it's merely a permissions error and you need to add the proper groups for your user.

If that doesn't work try

```
/usr/bin/alsamixer
sudo /usr/bin/alsamixer
```If that works it means the default bash session directories are messed up. (/usr/bin is not included).

I suspect it's a permissions issue.

Edit: this post should help you troubleshoot groups if it is indeed the case.
[http://ubuntuforums.org/showpost.php?p=9763052&postcount=2](http://ubuntuforums.org/showpost.php?p=9763052&postcount=2)

---

### Post by .... on 2011-07-26
> **tjones00 said:**
> I suspect it's a permissions issue.
I hope you're right, but I think the message is indicating no /dev/mixer, which means kernel module is not loading correctly. Run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by lkjoel on 2011-07-26
Try Sound Troubleshooting in my signature.

I think that this problem is because ALSA doesn't recognize the soundcards, or it isn't loaded.

---

### Post by Number1luda on 2011-07-27
> **.... said:**
> I hope you're right, but I think the message is indicating no /dev/mixer, which means kernel module is not loading correctly. Run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

this is what happens when I run the script


```
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14119: ignoring bad line starting with 'T")f&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14120: ignoring bad line starting with '&#65533;&#65533;#&#65533;&#65533;D!JR%'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14121: ignoring bad line starting with 'X&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14122: ignoring bad line starting with '&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14123: ignoring bad line starting with 'Hw&#65533;2%yl&#65533;z&#65533;<!&#65533;<&#65533;&#65533;&#65533;x&#65533;&#65533;,&#65533;];&#65533;w9&#716;m4'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14124: ignoring bad lin&#65533;?&#65533;,<&#65533;&#65533;_&#65533;&#65533;yT&#65533;&#65533;D&#65533;?&#65533;&#65533;&#65533;u+&#65533;R&#65533;"&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14125: ignoring bad line starting with '~&#65533;?&#65533;&#65533;u&#65533;
                        &#1896;S&&#1188;;+&#65533;&#65533;a0&#65533;&#65533;&#1727;&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;s&#65533;&#65533;P^&#65533;&#65533;&#65533;&#65533;C&#65533;B&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14126: ignoring bad line starting with '
                 &#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14127: ignoring bad line starting with '&#65533;#J
                   a&#65533;ZD,&#962;&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1378;B&#65533;&#65533;$&#65533;&#65533;2*tS&#65533;GkG|&#925;afB&#65533;&#65533;&#65533;&#65533;@&#65533;5*&#65533;&#65533;&#65533;
                                                                          1&#65533;&#65533;&#65533;4n&#65533;I1&#24145;RTPL&#65533;L&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14129: ignoring bad lin&#65533;&#1120;&#65533;&#65533;&#65533;5a,&#65533;a'th '
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14130: ignoring bad line starting with '&#65533;&#65533;HR&#65533;&#65533;&#65533;?&#65533;4&#65533;&#65533;&#65533;r!|?'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14131: ignoring bad line starting with '&#65533;c&#65533;Xa&#65533;I$&#65533;&#65533;&#65533;e&#65533;x&#65533;&#65533;E&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14132: ignoring bad line starting with 'm&#65533;&#65533;^&#65533;"&#65533;T'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14133: ignoring bad line starting with 'h&#65533;V&#65533;&#65533;&#488;&#65533;t0L5-xyD&#65533;&#65533;Ax"&#628;/Yx&#65533;A&#65533;&#65533;&#65533;&#65533;h~&#65533;]&#65533;$&#65533;&#65533;&#65533;&#971;&#65533;&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14134: ignoring bad line starting with 'gC'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14135: ignoring bad line starting with 'V"s&#65533;/&#65533;A&#1942;@
                          &#37300;8&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14136: ignoring bad line starting with '&#65533;Bg&#65533;&#65533;J"Z6&#65533;B
                             &#65533;&#65533;&#65533;NCw&#65533;&#65533;&#1754;&#65533;JM&#65533;&#65533;'&#65533;Ð&#65533;#&#65533;&#65533;&#65533;O&#65533;&#65533;}R&#65533;q"p&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14137: ignoring bad line starting with '&#65533;&#65533;&#1972;,B@&#65533;&#65533;
                          &#65533;(7:P/&#65533;EWo&#65533;$S>JPg&#65533;"'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14138: ignoring bad line starting with 'J&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14140: ignoring bad line starting with '&#65533;dB&#65533;Q&#65533;&#65533;9&#65533;=&#65533;@&#65533;&#65533;)P^{'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14141: ignoring bad line starting with '/&#403;v&#65533;*&#65533;&#65533;
&#65533;'GP&#65533;<H&#65533;&#65533;`|&#65533;&#65533;/l&#65533;#&#65533;&#65533;&#65533;(q&#65533;l&#65533;PHj-:&#65533;&#65533;&#65533;&#65533;&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14142: ignoring bad lin&#65533;)O*&#65533;&#65533;&#65533;&#65533;&#49296;&#65533;h&#65533;&#65533;&#65533;&#273;""H&#65533;&#65533;2&#1906;&#65533;IJ&#65533;&#65533;W"RH'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14143: ignoring bad line starting with '*&#65533;*'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14144: ignoring bad line starting with 'B&&#65533;&#65533;Y&#65533;&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;w&#65533;z&#65533;&#65533;x&#65533;&#65533;&#65533;T&#65533;&#65533;&#65533;^&#65533;byd&#65533;BD&#65533;:&#65533;z-E_&#65533;.P&#65533;&#65533;=K
                                                                     &#65533;P@!E&#65533;u&#65533;&#65533;&#65533;da&#65533;ó&#65533;E&#65533;8&#65533;&#65533;&#65533;#m>@%&#65533;&#65533;c&#65533;8&#65533;&#65533;q&#65533;&#65533;[&#65533;&#658;r#U~&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;KM*d&#65533;R&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14145: ignoring bad line starting with 'N&#65533;&#65533;&#65533;C%&#65533;H1&#65533;>r&#65533;A&#65533;;f&#65533;&#65533;f&#65533;4M&#65533;0&#65533;4&,9p&#65533;&#65533;&#65533;
                                                      &#65533;&#65533;w&#65533;&#65533;CH&#65533;&#65533;Q1&#372;M&#65533;&#65533;&#1304;KtP&#65533;cm&#65533;&#65533;(H&#65533;b"(&#65533;Ÿ&#65533;Hz&#65533;!)&#65533;&#65533;N&#65533;N$&#65533;1&#65533;#&#65533;&#65533;&#65533;A&#65533;&#65533;&#65533;"&#65533;&#65533;X'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14146: ignoring bad line starting with '&#65533;&#1772;&~&#65533;&#65533;&#65533;cg&#65533;]&#65533;e&#65533;"gH&#65533;&#65533;@X&#65533;Yq&#65533;&#65533;C'&#65533;&#65533;&#65533;1p&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14147: ignoring bad line starting with '&#65533;&#65533;KI

(&#65533;A&#65533;4U&#65533;              BR
        `a&#65533;&#65533;&#65533;E4&#65533;+Z9&#65533;(er&#65533;&#65533;&#65533;&#65533;6&#65533;F&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14148: ignoring bad line starting with '&#65533;B&#65533;~%&#65533;&#65533;{2&#65533;(y&#65533;&#65533;_&#65533;<&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;&#65533;`'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14150: ignoring bad line starting with '&#65533;&#65533;[&#317;EHMO<8g&#65533;lw&#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;&#65533;`&#65533;p&#65533;m&#65533;l1&#65533;2(&#65533;&#65533;&#65533;&#65533;cP&#65533;&#65533;&#65533;j&#65533;L&#65533;&#65533;oP&#65533;&#65533;&#65533;
                                                                            &#277;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14151: ignoring bad line starting with '&#65533;C#&#65533;&#65533;G.z4&#65533;&#65533;4,&#65533;&#65533;&#65533;:&b:0&#65533;&#65533;G)(bq3&#65533;,Qcn&#65533;&#65533;0!'HR&#65533;&#65533;&#65533;b&#292;&#65533;V4lJ&#65533;&#65533;&#65533;V&#65533;z6&#65533;q&#65533;&#65533;Q&#65533;X&#65533;0&#65533;"&#65533;eK&#1599;&#65533;&#65533;e&#65533;1&#65533;4Ul&#65533;&#65533;&#65533;i&#65533;-&#61956;8f&#65533;5&#65533;&#65533;&#65533;&#310;.A&#65533;}%+&#65533;u&#65533;i'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14152: ignoring bad line starting with 'r&#1045;4e&#65533;&#65533;E(D&#65533;&#65533;&#65533;&#65533;m&#65533;1&#65533;Z¢&#65533;
                                     P2'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14153: ignoring bad line starting with '&#65533;&#65533;&#65533;&#1420;0*&#1120;%CT&#65533;&#65533;0&#65533;&#65533;%&#65533;ShQ&#65533;0&#65533;
&#65533;]&#65533;k&#65533;&&#65533;&#65533;&#416;&#65533;'                                IV&#65533;&#65533;&#65533;L
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14154: ignoring bad line starting with '&#1137;'&#65533;i&#65533;&#65533;&#65533;&#65533;#mPM!&#65533;`&#65533;&#65533;*&#65533;0&#65533;v
                                          &#65533;&#65533;
                                            &#65533;&#65533;R<&#65533;,&#65533;&#65533;#&#65533;Dl@&#65533;LU&#65533;&#65533;&#65533;H&#65533;Li&#65533;&#65533;&#65533;R(&#65533;,]&#65533;R&#65533;B&#65533;
      @&#65533;&#65533;1
            .k!&#65533;&#65533;&#65533;$&#65533;3&#65533;&#65533;}&#1700;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14155: ignoring bad line starting with 'Sdn`&#65533;&#65533;@&#65533;h[&#65533;5UUUU'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14156: ignoring bad line starting with '&#65533;0&#65533;5X&#65533;k&#65533;(P&#65533;&#65533;h5&#65533;&#65533;we(&#65533;=&#65533;&#65533;h3E&#65533;FdANfDj0&#65533;&#65533;2K
                                                             $&#65533;h&#65533;=Z`&#65533;W-m&#65533;&#65533;.&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;&#65533;l&#65533;&#65533;&#65533;&#65533;&#65533;O&#65533;&#65533;0v&#65533;")&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14157: ignoring bad line starting with '&#65533;$&#506;#;&#549;%?7&#65533;>s$zJ&#65533;&#65533;6&#65533;&#65533;&#65533;r&#65533;cEn$&#65533;UR&#65533;&#1032;X&#65533;]&#65533;&#65533;&#65533;
                                                          &#65533;$rc&#65533;<h&#65533;&#65533;c&#65533;&#65533;&#65533;bX&#65533;9m+0G&#65533;b&#65533;;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;wu&#65533;&#65533;&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a&#49655;&#65533;&#65533;]!I!&#65533;&#65533;B&#65533;YA&#65533;&#65533;L&#65533;&#65533;&#65533;&#65533;d&#65533;)x&#65533;@&#65533;&#65533;7&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;@&#1099;&#65533;&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;IaT@^&#65533;&#65533;v&#65533;9s&#1827;&#1009;Ib&#65533;&#65533;S~G&#65533;t8&#65533;1_'&#65533;&#65533;~03%&#65533;&#65533;3&#65533;&#65533;()'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14158: ignoring bad line starting with '&#65533;&#65533;3Q&#65533;&#65533;&#65533;
                         &#65533;&#65533;f&#65533;&#65533;I:|X&#65533;&#65533;&#65533;&#65533;"9U|jj&#65533;4R&#65533;&#65533;$@&#65533;&#65533;&#65533;M+&#65533;Y&#65533;&#65533;uJ&#1038;&#65533;5UU&#65533;&#65533;&#65533;N:&#65533;&#65533;'T]&#65533;&#65533;N&#1120;&#65533;&#65533;6&#65533;s&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14159: ignoring bad line starting with ''&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;"{&#65533;G&#1094;$&#65533;E1&#65533;A&#65533;&#65533;&#65533;B&#65533;VQ&#65533;"v&#65533;Tj&#65533;he$&#65533;&#65533;WM&#65533;&#18858;"&#65533;16&#65533;h(&#65533;G&#65533;&#65533;Ea&#65533;&#65533;2[&#65533;&#65533;lcJd&#65533;e'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14160: ignoring bad lin'LC$&#65533;&#65533;&#65533;ITF&#65533;^&#65533;&#65533;&#65533;&#65533;.&#65533;sRR&#65533;B+O&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14161: ignoring bad linAPnD``)&#65533;,&#65533;with '&#65533;^&#65533;&#65533;&#65533;H?Hw&#65533;&#65533;&#65533;6&#65533;P"&#65533;pK&#65533;&#65533;f&&#65533;&#956;&#65533;}'&#65533;u&#65533;&#42258;
           5/'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14162: ignoring bad line starting with 'h&#65533;3&#65533;H&#65533;&#2045;AG&#65533;D>&#65533;
                               &#65533;&#65533;"?&#65533;&#65533;v&#65533;&#65533;Ry4&#135;#E&#65533;&#65533;&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14163: ignoring bad line starting with '&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14164: ignoring bad line starting with ';
                  &#65533;&#65533;ghS&#65533;&#65533;X&#65533;&#65533;F(D"&#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;aK&#65533;#.&#65533;&#65533;&#334;E&#65533;90;2l&#65533;&#65533;l&#65533;w&#65533;0&#65533;&#65533;&#65533;'W&#65533;&#65533;%4R-J'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14165: ignoring bad line starting with '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;L#&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14166: ignoring bad line starting with '&#65533;Ot&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14167: ignoring bad line starting with '&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#40156;eQz&#65533;B*)&#65533;TC&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14168: ignoring bad line starting with '&#65533;&#65533;&#65533;&#65533;`$]&#65533;8(J&#65533;&#65533;D&#65533;P&#65533;&#65533;&#65533;&#65533;DJO&#65533;
                                              '
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14169: ignoring bad lin&#65533;&#1484;'tarting with '&#65533;a"A{b&#65533;&#1206;&#65533;=
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14170: ignoring bad line starting with 'A&#65533;&#65533;p&#65533;1&#65533;M&#65533;&#65533;o5&#65533;&#65533;&#65533;&#65533;G22)&#65533;&#65533;&#65533;3&#65533;uq&#65533;&#65533;)&#65533;F&#65533;&#65533;z&#363;&#65533;lQ&#65533;&#65533;&#132;&#65533;,(A`&#65533;
                                                                           &#65533;2&#65533;&#65533;I&#65533;GY4&#65533;")Xa&#65533;&#65533;&#65533;&#65533;`A&#65533;T&#65533;&#65533;
a&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14171: ignoring bad line starting with '2&#65533;2&#392;5T&#65533;7&#65533;&#65533;4M&#65533;&#65533;&#65533;)&#65533;8&#65533;&#65533;&#65533;[F&#65533;;j&#65533;fa'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14172: ignoring bad line starting with 'm&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14173: ignoring bad line starting with '&#65533;&#65533;Ko@&#65533;Ä&#65533;$&#65533;n&#65533;&#65533;&#65533;)&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14174: ignoring bad lin&#65533;&#65533;S&#65533;&#65533;.T&#65533;&#65533;V&#65533;&#65533;(bjR'&#65533;&#65533;&#65533;&#65533;k%&#65533;]&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;cF&#65533;-&#65533;"
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14175: ignoring bad line starting with ''
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14176: ignoring bad line starting with '&#65533;#i&#65533;4Z$&#65533;p&#65533;&#65533;J0&#65533;&#65533;&#65533;H&#65533;&#65533;5&#1866;jH'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14177: ignoring bad line starting with '`&#65533;Gx&#65533;&#65533;&#65533;;s&#65533;&#65533;xN|&#65533;(@&#65533;B'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14178: ignoring bad line starting with 'J&#65533;&#65533;*'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14179: ignoring bad line starting with '&#65533;I&#65533;&#65533;&#65533;¶&#65533;+&#65533;ne&#366;&#65533;y&#1436;g&#65533;k'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14180: ignoring bad line starting with '%#U88,&#65533;"&#65533;&#65533;&#65533;&#65533;F!&#65533;b&#65533;R&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14181: ignoring bad line starting with ''
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14182: ignoring bad line starting with '&#65533;&#65533;
                   #&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&&#65533;&#65533;d&#65533;O&#65533;KD&#65533;`&#65533;5&#65533;&#65533;&#65533;
                                               s0X)&#65533;&#65533;b)$&#65533;$&#65533;vP<&#65533;Nd&#65533;m&#65533;P&#65533;&#65533;W&#65533;>&#65533;q&#65533;C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I"A&#65533;&#65533;&#65533;&#65533;Xt)'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14184: ignoring bad line starting with 'Q&#65533;Kc2r6&#65533;0&#65533;"&#65533;&#65533;*&#65533;$&#65533;&#65533;
                                      &#65533;&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14185: ignoring bad line starting with '&#65533;hP&#65533;R&#65533;R&#65533;3B&#65533;Ji'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14187: ignoring bad line starting with '&#65533;*&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14188: ignoring bad line starting with 'wM&#65533;%'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14189: ignoring bad line starting with '$B'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14190: ignoring bad line starting with 'E&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14191: ignoring bad line starting with 'K&#65533;&#65533;|&#65533;&#65533;&#65533;sm'&#65533;&#65533;G'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14192: ignoring bad line starting with 'F&#65533;'7&#65533;&#65533;o"&#65533;g&#65533;&#65533;g&#65533;`&#65533;&#65533;$&#65533;d&#65533;&#65533;&#65533;&#65533;R&#65533;b$C
                                                   &#65533;B0:&#4896;b]&#65533;&#65533;&#65533;"P&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14193: ignoring bad line starting with 'C&#65533;&#65533;&#65533;G&#65533;.&#65533;B&#65533;&#65533;&#65533;&#65533;&#65533;H&#65533;]&#65533;yS&#65533;<&#65533;&#65533;&#65533;[s&#65533;&#65533;@&#65533;J&#65533;&#65533;+&#65533;&#65533;&#65533;&#65533;('
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14194: ignoring bad line starting with 'X'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14195: ignoring bad line starting with '&#65533;&#65533;&#65533;@&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14196: ignoring bad line starting with 'x&#65533;5C6,&#65533;&#65533;&#65533;&#65533;&#65533;
                                `&#65533;a&#65533;D@&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14197: ignoring bad line starting with 'FFB&&#65533;)I&#65533;B&#65533;&#65533;aJ&#65533;Qd&#65533;%N&#65533;D&#65533;X6p&#65533;&#65533;&#65533;&#65533;/&#65533;V&#65533;~X&#65533;&!&#65533;&#65533;&#65533;{z$&#65533;~&#65533;b>E&#65533;&#65533;&#65533;u&#65533;&#65533;)!&#65533;&#65533;
  v_'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14198: ignoring bad line starting with '.&#65533;YX$1&#65533;W&#1455;&#1672;&#65533;Y'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14199: ignoring bad line starting with '/&#65533;0Q&#1113;&#65533;&#65533;@&#65533;6pBl|'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14200: ignoring bad line starting with '@&#65533;sp^$9&#65533;&#65533;d&#65533;&#65533;/&#65533;or&#65533;S!&#65533;&#65533;&#65533;x&#3037;&#65533;c&#65533;&#65533;&â&#65533;O&#65533;PI~&#65533;&#65533;&#65533;&#65533;&#65533;/d&#65533;>&#501;?&#65533;&#65533;&#65533;;&#65533;;7|a&#65533;
&#65533;:&#65533;&#65533;7M3&#65533;5&#65533;&#65533;&#65533;>&#65533;W&#65533;!&#65533;&#65533;&#65533;7Ts'&#65533;sQ&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14201: ignoring bad line starting with 'N5'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14202: ignoring bad line starting with '7&#65533;a&#1473;&#65533;&#65533;D&#65533;U'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14203: ignoring bad line starting with HMb&#65533;?&#65533;@f&#65533;&#65533;-&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;t&#65533;&#518;&#2018;@&#65533;&#65533;(&#65533;&#65533;wf$&#65533;a?&#65533;m&#65533;&#65533;Gc&#65533;&#65533;H&#65533;%&#65533;&&#65533;&#65533;M$&#65533;6Sl&#65533;>&#65533;eT&#65533;85;Xc&#65533;
        &#65533;&#65533;&#1448;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;8eL&#65533;&#65533;&#65533;d!&#65533;&#65533;tbm&#65533;pr(&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14204: ignoring bad line starting with '/&#65533;&#65533;P@&#65533;&#358;&#65533;&#65533;H&#65533;&#65533;"Ei&#344;z&#65533;&#65533;&#65533;I`~&#65533;CB&#65533;F'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14205: ignoring bad line starting with 'G&#65533;y&#65533;G&#65533;qu&#65533;&#65533;&#65533;f&#65533;D&#65533;$&#65533;
                                    mAz&#65533;&#65533;&#65533;&#65533;Q;&#65533;a&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14206: ignoring bad line starting with '&#661;&#65533;3"&#65533;r'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14207: ignoring bad line starting with 'c&#65533;&#65533;&#65533;>&#65533;I&#295;&#65533;w&#65533;B&#65533;}&
                                 &#65533;&#65533;&#65533;
                                    &#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14208: ignoring bad lin{dm&#65533;&#65533;C&#65533;&#65533;'g with 'agy&#65533;&#65533;&#65533;;u%t
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14209: ignoring bad line starting with '0&#1638;&#65533;T4&#65533;]&#65533;&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;J(h&#65533;&#65533;&#65533;&#65533;4D&#65533;&#945;&#272;!%fI3
                                                    D&#65533;&#65533;fB%)%&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14210: ignoring bad line starting with 'I&'0&#22572;&#65533;_k&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;M&#65533;&#65533;W&#65533;&#65533;2
                                        &#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;YbT&#65533;+&#65533;f&#65533;R&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;!&#65533;F''
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14211: ignoring bad linS&#65533;&#65533;+&#65533;&#65533;%+&#65533;&#65533;&#65533;r&#65533;P&#65533;|Z&#65533;&#65533;&#65533;J$w=&#65533;9:&#65533;&#1384;&#65533;&#65533;&#65533;I&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14212: ignoring bad line starting with '&#65533;"&#65533;&#65533;$9e%&#65533;!&#65533;m&#65533;W&#65533;&#65533;j&#65533;&#510;&#65533;&#401;&#524;&#65533;($&#65533;&#65533;f&#65533;&#65533;i~&#65533;L&#65533;4&#65533;$Ij&#392;M&#65533;&#65533;&#65533;&#65533;&#65533;X9&#65533;G&#65533;T&#272;&#65533;A&#1544;&#65533;|'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14213: ignoring bad line starting with 'S
&#65533;M&#65533;#'             *d!&#65533;y&#65533;&#65533;&#65533;1&#65533;G&4m
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14214: ignoring bad line starting with 'l&#65533;&#65533;D&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#898;kDL&#65533;:&#65533;&#65533;&#65533;"L&#65533;&#65533;&#65533;&#65533;)'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14215: ignoring bad line starting with '&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14216: ignoring bad lin.&&#65533;&#65533;lCE&#65533;A&#65533;&#65533;&#65533;R&#65533;mc6&#65533;0&#65533;Np&#65533;,&#65533;&#65533;1&#65533;&#65533;""&#65533;=&#65533;n&#65533;&#65533;&#65533;&#65533;&#1626;&#65533;&#65533;&#65533;&#65533;R&#65533;"&#65533;&#65533;!0|&#65533;&#1757;&#65533;$@A&#65533;
                    0M$&#65533;Dm&#65533;D?&#65533;64&#65533;t&#65533;cR&#65533;&#65533;&#65533;S&#65533;&#65533;@&#65533;&#133;h&#65533;oFB
                                                      R&#65533;&#65533;-=R?&#65533;h:;F&#65533;[u&#65533;0|d&#65533;&#65533;C.Z&#65533;!&#65533;b&#65533;&#65533;(1*&#65533;&#65533;Z&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14217: ignoring bad line starting with '&#65533;[09&#65533;A6cH&#65533;&#65533;&#65533;&#65533;(8%kI&#65533;D&#65533;]``51lr.&#65533;&#65533;pJ&#65533;
                                                      &#65533;&#65533;@&#519;]&#65533;(b$&#65533;&#65533;S&#65533;UQY&#65533;&#65533;6@&#65533;W&#65533;&#65533;q8&#65533;x)&#65533;&#65533;4'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14218: ignoring bad line starting with 'ED&#65533;A&#65533;M-'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14219: ignoring bad line starting with '7P&#1812;h+&#65533;D&#65533;4&#65533;;[E&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14220: ignoring bad lin&#65533;hLI-&#65533;&ing with ';q&#65533;&#65533;&#65533;m&#65533;dd~
       gQ&#65533;:&#65533;
            5'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14221: ignoring bad lin&#65533;&#65533;starting with '
  '&#65533;q:B&#65533;&#65533;hpZE&#396;&#65533;hJ'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14222: ignoring bad lin&#65533;X&#65533;<:&#65533;2h&#65533;'ith '`&#1317;&#65533;M
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14223: ignoring bad line starting with 'Af&#65533;!&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;'DL&#65533;0|&#65533;0$:&#65533;&#65533;w&#65533;&#65533;&#65533;A&#65533;3C&#1238;&#65533;&#65533;&#65533;&#65533;&#65533;lw&#65533;>P&#65533;7&#65533;nU(&#996;&#65533;,c&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;:b{!&#65533;&#65533;&#65533;m&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14224: ignoring bad line starting with '?9'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14225: ignoring bad line starting with '&#65533;Y:&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533;4&#65533;Q$'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14226: ignoring bad line starting with '&#65533;g&#65533;?&#65533;&#65533;Y(&#65533;B$c&#65533;R&#65533;&#65533;h!&#65533;&#65533;&#65533;fX:&#779;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14227: ignoring bad line starting with '&#65533;flF&#65533;r&#65533;uHADJ$&#65533;IU0P&#65533;EJ*&#65533;&#65533;|&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14228: ignoring bad line starting with '&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14229: ignoring bad line starting with '!&#65533;&#65533;&#65533;u&#65533;&#65533;q&#65533;B&#65533;&#65533;&#65533;&#65533;'`&#65533;v&#65533;&#65533;&#65533;;&#65533;&#65533;N^(.i&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14230: ignoring bad line starting with '8&#65533;&#65533;y&#65533;$&#65533;E&#65533;8&#65533;&#65533;&#65533;:&#845;+&#65533;HR0&#65533;,e&#65533;`&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14231: ignoring bad line starting with 'R&#65533;&#65533;&#65533;&#65533;L*&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14232: ignoring bad line starting with 'K`&#65533;3&#65533;BP&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14233: ignoring bad line starting with '@-V&#65533;hTb&#1545;b&#65533;&#65533;&#65533;&#65533;W&#65533;Y&#65533;&#65533;&#1951;#&#65533;&#65533;&#65533;;&#65533;b'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14234: ignoring bad line starting with '&#65533;1&#65533;&#65533;x&#65533;m&#65533;<&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;&#65533;fo&nRt&#65533;&#65533;&#65533;&#65533;,)KG&#1885;y&#65533;s&#65533;&#65533;>&#1351;&#65533;bM&#65533;M'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14235: ignoring bad line starting with '&#65533;&#65533;?4&#65533;W'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14236: ignoring bad line starting with '&#65533;&&#65533;|~S&#65533;&#65533;-L&#65533;&#65533;&#65533;Q&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533;&#335;x&#65533;N&#65533;7UK&#65533;&#65533;B+3&#65533;e'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14237: ignoring bad line starting with '&#65533;&#65533;&#65533;&#65533;&#1337;&&#65533;]bq&#65533;&#65533;e[&#65533;1&#65533;&#65533;&#65533;3L&#65533;&#65533;&#65533;d]cN&#65533;&#65533;&#65533;|R&#65533;Iu&#65533;+&#65533;&#65533;^S&#65533;#&#65533;d!'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14238: ignoring bad line starting with 'Z&#65533;=&#1489;&#65533;m&#65533;&#65533;`sM&#65533;&#65533;)&#65533;&#65533;&#;t&#1884;&#65533;&#65533;V&#65533;y:4&#497;&#65533;@&#65533;?V7&#65533;&#1390;&#65533;&#65533;XL|&&#65533;~&#65533;]&#65533;w&#65533;&#65533;&#65533;&#65533;w,.&#65533;&#65533;7:&#65533;&#65533;&#65533;&#2038;l&#65533;9&#65533;&#65533;&#65533;q&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;:9~&#65533;;'<x0&#65533;&#65533;&#65533;&#65533;+&#65533;jWd&#65533;&#65533;9JSx&#65533;&/&#65533;&#65533;|&#65533;G'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14239: ignoring bad line starting with '[&#65533;&#65533;L&#65533;Lf&#65533;&#65533;I&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;&#637;5Q&#65533;#A&#65533;wf&#972;&#65533;1;&#65533;&#65533;q7&#65533;&#65533;s&#65533;&#65533;j&#65533;&#65533;&#65533;t&#65533;IZ&#65533;&#65533;&#65533;&#65533;si6t&#65533;e&#65533;&#65533;&#65533;&#65533;%FB/&#65533;J4P4&#65533;&#53369;2&#65533;&#65533;&#65533;&#65533;&#65533;7=&#8992;&#65533;&#65533;&#65533;V&#65533;Y-)&#65533;&#65533;&#65533;&#65533;lg&#65533;3&#1847;F&#65533;r&#65533;&#65533;
                                                       YLL&#65533;['
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14240: ignoring bad line starting with '&#65533;&#65533;&#65533;zd&#65533;&#65533;
                          &#65533;(C&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14241: ignoring bad lin&#65533;&#65533;&#65533;@&#65533;&#1527;+&#65533;!&#65533;&#65533;&#138;2' 'GZ&#65533;&#65533;s&#65533;&#65533;|&#65533;&#65533;&#65533;&#65533;&#65533;gR&#927;d&#65533;I&#65533;b&#65533;F&#65533;>_/&#65533;R&#65533;&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14242: ignoring bad line starting with '&#65533;*Y'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14243: ignoring bad line starting with '&#65533;$&#65533;%PU^&#65533;^{&#65533;g&#65533;6
                                &#65533;5&#65533;
                                    &#65533;&#65533;KH&#65533;!/&#65533;&#65533;&#2014;E>0s&#65533;q&#65533;$'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14244: ignoring bad line starting with 'J^A&#65533;Z&#65533;&#65533;!I
                          &#65533;&#65533;[H&#65533;P&#65533;&#65533;&#65533;im6&#65533;&#65533;&#65533;K-a&#65533;[X&#65533;!&#65533;&#65533;<f&#1076;&#65533;@&#65533;D&#65533;2&#65533;&#558;&#65533;CP&#314;&#65533;&#65533;&#65533;
                                                                           p{&#65533;&#65533;&#65533;L&#65533;b"*&#65533;@&#65533;0('
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14245: ignoring bad line starting with '&#65533;(&#65533;&#65533;Z&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;+&#65533;4&#65533;&#65533;&#65533;j&#65533;&#65533;7&#65533;&#65533;UDBQE&#65533;#&#65533;>(&#65533;>&#65533;a'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14246: ignoring bad line starting with 'QXM&#65533;8&#65533;
                        .&#65533;a&#65533;&#65533;&#65533;&#529;&#65533;x)&#65533;xj&#65533;&#65533;u56&#65533;Sgq"&#1898;Nd&#1454;[&#65533;&#65533;&#65533;&#1892;i&#65533;l'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14247: ignoring bad line starting with 'aa)&#37617;&#65533;&#65533;&#65533;&#65533;&#65533;cm&#34842;joec=!&#65533;5&#65533;v&#65533;5&#65533;E;&#65533;nr
                                                        ^@&#65533;&#65533;Wqt&#65533;S'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14248: ignoring bad line starting with '|o,(&#65533;1h&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14249: ignoring bad line starting with 'w&#952908;&#65533;!v
                      ;b6?e&#65533;&#65533;/&#65533;
                                &#65533;&#65533;]&#65533;&#65533;&#65533;drI;KT&#65533;[&#27988;M$&#65533;EUUUQMQUUTU1&#65533;&#65533;$&#65533;j&#65533;$m&#65533;&#65533;&#65533;m&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14250: ignoring bad line starting with '!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1576;33X&#65533;{&#65533;[s&#65533;&#65533;&#65533;&#908;&#65533;Bk&#65533;&#65533;5'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14251: ignoring bad line starting with '&#65533;
                  &#65533;G&#2881;&#65533;&#65533;v/!m>&#65533;&#65533;NTf&#65533;[&#65533;qV&#65533;&#65533;&#65533;C-kk$9Q&#65533;&#65533;&#65533;c&#65533;&#65533;&#1445;
                                                          vfS&#65533;{&#65533;&#65533;r&#65533;-9Qt&#65533;&#65533;&#1594;&9&#65533;C&#65533;r%&#1894;4&#65533;&#65533;q&#65533;FZU&#65533;&#65533;&#65533;&#65533;&#65533;11&#65533;bF"&#65533;BR&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?K&#65533;3w&#65533;mu&#65533;&#1942;&#65533;C&#65533;&#65533;&#65533;&#65533;KvP&#65533;^"&#65533;&#65533;D%r&#65533;1j:&#65533;&#65533;'&#65533;&#65533;"&#65533;8&#65533;(ry%X`JWl,!n&#149;&#1291;&#65533;b&#65533;&#65533;gg&#65533;&#65533;Rr&#65533;i&#65533;&#65533;&#65533;5&#65533;4&#65533;&#65533;&#1820;&#65533;q2&#65533;&#65533;&#65533;k&#65533;l'&#65533;&#65533;`}&#65533;&#65533;&#65533;3&#65533;&#1450;v=&#65533;&#65533;&#1049;!&#65533;&#65533;L&#923693;&#65533;r&#65533;X&#65533;&#65533;
'(B     :kn&#65533;&#65533;$&#65533;.&#65533;&#852;
   "&#65533;S&#65533;&#65533;&#65533;PF&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14252: ignoring bad line starting with '!1]w4V&#65533;&#14400;9U&#65533;C
&#1659;f&#65533;<&#65533;&#65533;&#65533;&#65533;&#65533;&#1293;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;vfLF#&#65533;&#65533;&#65533;&#65533;&#65533;'      &#65533;u&#65533;Cz&#65533;&#65533;6&#65533;&#65533;&#65533;&#65533;&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14253: ignoring bad line starting with '6fl&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14254: ignoring bad line starting with '&#65533;&#65533;&#65533;:{&#65533;&#65533;;&#65533;&#65533;s'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14255: ignoring bad line starting with ')(&#65533;&#65533;&#65533;&#65533;P'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14256: ignoring bad line starting with '&#65533;q'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14257: ignoring bad line starting with '&#65533;R&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;Z&#65533;@|&#65533;&#65533;&#65533;&#65533;&#154;&#65533;7&#65533;W&#65533;@&#65533;t&#65533;&#65533;-&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14258: ignoring bad line starting with '&#65533;&#65533;&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14259: ignoring bad line starting with 'S&#65533;4&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;Fdr&#65533;^}&#65533;&#65533;&#1060;AP!&#65533;&#65533;&#65533;S&#65533;&#65533;&#65533;e'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14260: ignoring bad line starting with 'd'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14261: ignoring bad line starting with 'r
                  E&#65533;
                     9wF&a(&#65533;iX&#65533;e,gV&#65533;XT&#65533;&#1203;D<A&#65533;&#65533;F"G)H'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14262: ignoring bad line starting with ')i&#65533;C'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14263: ignoring bad line starting with '%&#65533;&#65533;&#65533;&#65533;&#65533;7{_sA&#65533;"&#65533;`&#65533;C'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14264: ignoring bad line starting with '&#65533;&#65533;&#65533;&#65533;&#65533;U!&_#&#65533;&#65533;&#888;&#65533;Sz'&#65533;&#65533;&#65533;9t&#65533;&#65533;&#65533;&#65533;*&#65533;M&#1521;&#65533;&#65533;&#65533;&#65533;
                                                      &#16802;JI&#65533;9&#65533;&#65533;&#65533;^&#65533;&#65533;8XMN&#65533;8&#65533;q&#65533;&#1835;_&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;&#65533;t1&#65533;&#1628;F&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14265: ignoring bad line starting with '&#65533;dv'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14266: ignoring bad line starting with 'Sd1&#65533;&#65533;,4&#65533;&#65533;w&#65533;&#65533;&#65533;+&#65533;D&#65533;L&#65533;0&#65533;&#65533;&#65533;&#65533;be
                                             =&#65533;
                                               (&#65533;)&#65533;&#65533;c3HI?XM'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14267: ignoring bad line starting with '?V&#65533;&#65533;m&#65533;'"K13&&&#65533;i&#65533;&#65533;&#65533;&#65533;i&#65533;&#65533;i&#65533;&#65533;&#65533;
                                              Hx&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14268: ignoring bad line starting with '&#65533;&#65533;&#65533;3Vd8&#65533;(&#1808;I6<g&#362;+&#65533;&#65533;b&#65533;&#65533;&#65533;'Kv'3&#65533;&#65533;!9&#65533;q&#65533;&#65533;~&#65533;&#961;&#1803;&#65533;&#65533;'8&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14269: ignoring bad line starting with '&#65533;>&#65533;^8j&#65533;&#65533;<ZD`OS9/~
                                   &#65533;!&#1333;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14270: ignoring bad line starting with '&#1544;&#65533;&#65533;`&#65533;&#65533;$UK(^W&#65533;^Ln$&#65533;Bs&#65533;9&#65533;;&#65533;&#788;<qq&#1554;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14271: ignoring bad line starting with '&#65533;&#65533;&#65533;:&#65533;ZY&#65533;&#65533;&#65533;s&#65533;u&#65533;]F67&#65533;F(^"&#65533;&#65533;&#65533;E'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14272: ignoring bad line starting with 'z&#65533;&#65533;s&#65533;&#65533;&#65533;1&#65533;$&#1158;&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;&#1643;qcH@=c9&#65533;y&#65533;&#65533;$dCf&#65533;&#65533;o&#65533;&#65533;&#65533;:"/&#65533;c&#65533;Ji&#65533;&#65533;l&#65533;Ze&#65533;i
                                                                              4aX&#65533;&#65533;dQ'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14273: ignoring bad line starting with '
                   &#65533;^kRj&#65533;&#65533;&#65533;&#65533;tA&#65533;#|-&#65533;&#65533;?&#65533;V&#65533;"-&#65533;&#65533;[&#65533;&#272;f&#65533;Q&#65533;(&#65533;&#65533;&#65533;&#65533;Q&#65533;&#65533;M&#65533;E6M&#65533;;Ait&#65533;W&#65533;&#65533;X*'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14274: ignoring bad line starting with 'û&#65533;&#65533;/@&#65533;&#65533;azBp&#65533;¨&#65533;^>8&#65533;&#65533;&#65533;8&#65533;,&#65533;&#65533;e&#1636;9&#65533;5;3!&#65533;&#65533;@,;&#65533;&#65533;z&#65533;`bV
                                                                        nc#&#65533;v*a)-&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14275: ignoring bad line starting with '3&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14276: ignoring bad line starting with 'PL&#268;&#65533;<&#65533;m&#65533;&#65533;R&#65533;J&#65533;~TS&#65533;8&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14277: ignoring bad lin' starting with '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@N&#65533;&#65533;&#65533;&#65533;%&#65533;`&#65533;&#65533;&#65533;&#65533;^a&#65533;&#65533;&#65533;&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14278: ignoring bad line starting with '&#65533;DW&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;j'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14279: ignoring bad line starting with '&#65533;&#65533;&#65533;uf&#65533;*&#65533;&#65533;0"&#65533;&#65533;&#65533;)C&#65533;
                                   &#65533;&#65533;a&#65533;&#65533;C$&#65533;lflT&#65533;m&#65533;&#65533;&#65533;&#65533;b&#65533;&#65533;"S"&#65533;6Z&#65533;&#65533;cx?&#65533;h&#65533;('
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14280: ignoring bad line starting with '&#65533;&#65533;XyWO''
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14281: ignoring bad line starting with '&#65533;&#65533;G&#65533;o&#65533;&#65533;Lfz&#65533;&#617;&#65533;&#65533;.&#65533;AC&#65533;&#65533;*&#65533;"?&#65533;!"&#65533;y<A&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;l.D&#65533;&#1071;&#65533;&#65533;&#65533;&#1352;X@)vh&#65533;b&#65533;Wo)0&#65533;3&#65533;&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14282: ignoring bad line starting with '&#65533;Q&#65533;&#65533;&#65533;<&#65533;'&#65533;%'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14283: ignoring bad line starting with '$&#65533;&#65533;01&#155;0&#65533;&#65533;&#65533;k@&#65533;n&#65533;-
                                    &#65533;I!@U@&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14284: ignoring bad line starting with 'D&#65533;&#1415;W'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14285: ignoring bad line starting with 'N&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14286: ignoring bad line starting with '&#65533;i=&#65533;xw3&#65533;@&E&#65533;P&#65533;&#65533;'&#65533;&#65533;
                                       Q&#65533;EX&#65533;-&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14287: ignoring bad lin&#65533;&#65533;:E<zn"`|'th '&#65533;u&#65533;&#65533;&#65533;if&#65533;J&#65533;)&#65533;&#65533;4&#65533;&#65533;}2&#65533;&#65533;X&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;&#65533;;g&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14288: ignoring bad line starting with '(j&#65533;)#"&#65533;[&#65533;&#65533;&#65533;&#65533;}6&#65533;(Ji&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14289: ignoring bad line starting with '&#65533;2&#65533;&#65533;F&#676;&#65533;&#65533;(F&#65533;/&#65533;&#65533;&#65533;&#65533;=%&#65533;&#1348;&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14290: ignoring bad line starting with 'z`&#65533;-r&#65533;i'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14291: ignoring bad line starting with 'B&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14292: ignoring bad lin&#65533;9&#1030;&#65533;Y&#65533;5&#65533;&#65533;&#65533;h&#65533;&#65533;u&#65533;l0{4&#65533;&#65533;&#65533;&#65533;peR&#65533;&#65533;&#65533;&#65533;~&#1044;&#65533;|&#65533;&#65533;&#65533;|J&#65533;!&#65533;&#65533;,L&#65533;&#65533;!@'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14293: ignoring bad line starting with '&#1137;&#65533;l&#65533;&#65533;cfHK&#65533;c,&#65533;&#65533;&#65533;&#1705;&#65533;"&#65533;"'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14294: ignoring bad line starting with 'Q&#65533;&#65533;6&#65533;E+_7&#65533;&#65533;9&#642;2w&#65533;%&#65533;&#65533;B4&#65533;&#65533;D&#65533;o'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14295: ignoring bad linE&#65533;&#65533;8Þc"&#65533;&#11778;&#65533;n&#65533;K~&&#65533;?X&#65533;&#65533;&#65533;&#65533;S&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14296: ignoring bad lin&#65533;&#65533;A&#65533;'rting with '6&#65533;&#65533;&#65533;&#65533;K&#65533;&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14297: ignoring bad line starting with '&#65533;&#498;*&#1627;&#586;&&#65533;&#65533;M&#65533;&#65533;m&#65533;Dm&#65533;;9-~:&#65533;&#65533;fr9&#65533;FT&#65533;r&#65533;NTy/&#65533;&#65533;F&#65533;&#65533;&#1771;ta&#65533;&#65533;z&#65533;e9sP):X&#65533;`&#65533;&#65533;&#65533;v&#65533;xC4&#65533;
&#65533;CS&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;Z&#65533;K&#65533;&#65533;&#65533;&#65533;3&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'W&#65533;
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14298: ignoring bad line starting with 'i&#65533;&#65533;<&#65533;9H&#65533;J&#65533;@&#65533;&#65533;eM&#65533;&#65533;&(&s&P&#65533;&#65533;&#65533;&#65533;j&#65533;"%&#65533;&#65533;a&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;eV&#65533;BB&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14299: ignoring bad line starting with 'GR&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14300: ignoring bad line starting with '5%*&&#65533;&#65533;&#65533;&#65533;H&#65533;&#65533;Id&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;O"V'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14301: ignoring bad line starting with 'Y&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;}&#65533;&#65533;?&#65533;&#65533;&#65533;i&#1002;&#65533;1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?n&#65533;*'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14302: ignoring bad line starting with 'K&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14303: ignoring bad line starting with '?<&#65533;&#65533;`C&#65533;&#65533;~&#257;&#65533;5&#65533;NGw&#65533;;'&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;&#65533;8~&#65533;&#65533;<&#65533;&#65533;?&#65533;&#65533;&#65533;&#65533;<H&#65533;&#65533;&#65533;<&#65533;2R&#65533;G&#65533;#&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14304: ignoring bad lin&#65533;&#65533;o&#65533;&#65533;}&#65533;&#65533;&#65533;$&#65533;.l&#65533;mqd&#65533;e#[&#307;&#65533;kh&#65533;&#65533;o,O&#65533;
                      &#65533;&#65533;&#65533;&#65533;$_=&#65533;G[&#65533;H&#65533;Pp&#65533;"Du&#145;W&#65533;&#671;&#65533;UNb&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14305: ignoring bad line starting with '&#65533;&#65533;7&#65533;Yx&#65533;&#65533;&#65533;S]A2d&#65533;&#65533;&#65533;O&#65533;n&#65533;&#65533;&#65533;?&#65533;&#65533;eF[2&#65533;&#1017;&#65533;&#65533;&#65533;~&#65533;&#65533;s&#65533;&#65533;&#65533;?&#65533;&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9&#65533;&#65533;|8;&#65533;T&U]&#65533;&#65533;&#65533;/&#65533;~&#65533;k&#65533;1b&#65533;/&#65533;&#65533;8p`T>Wg&#65533;&#851;T&#65533;r&#65533;&#458;&#65533;&#65533;x}1&#65533;"!&#65533;&#65533;UcB&#65533;&#65533;&#65533;&#65533;&#1955;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B3'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14306: ignoring bad line starting with 'F&#65533;Y&#65533;~&#65533;A&#65533;&#65533;&#65533;&#65533;A&#65533;BF&#65533;O&#65533;&#65533;(;&#65533;p&#373;4&#65533;E&#65533;ah&&#65533;7^&#65533;@'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14307: ignoring bad line starting with '"!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;{&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;0u&#65533;&#65533;&#65533;&#65533;&#65533;>e&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#740;6&#65533;!&#65533;?&#65533;w&#65533;d6&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14308: ignoring bad line starting with ''&#65533;#&#65533;+&#65533;&#1797;&#65533;ek&#65533;9K&#65533;&#65533;&#65533;I6&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;8&#65533;v?&#65533;òG&#65533;&#65533;)&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;5&#65533;b&#65533;d&#1303;&#65533;m&#65533;&#65533;&#65533;&#1736;&#65533;&#65533;&#65533;&#65533;x&#65533;|'h&#65533;?/&#65533;&#65533;&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;O&#689;&#65533;&#65533;&#65533;eeyK4d&#65533;v&#65533;&#65533;,&#65533;&#65533;~)&#65533;AG&#65533;&#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;pi&#65533;&#65533;&#65533;c&#65533;q&#65533;T&#65533;w&#65533;S&#65533;&#65533;&#65533;~o&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14309: ignoring bad line starting with '&#65533;i&#65533;&#65533;&#65533;&#65533;6}&#65533;&#65533;&#65533;2(DBo)&#65533;8&#65533;?&#65533;&#1119;&#65533;&#65533;*&#65533;>&#65533;&#65533;J&#65533;&#65533;&#65533;K1qNM&#65533;&#65533;&#65533;&#65533;&#729;&#65533;o&#65533;&#65533;5&#1828;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1031;&#65533;&#65533;&#65533;&#65533;D'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14310: ignoring bad line starting with '&#65533;
                   &#65533;!&#65533;&#65533;Z&#65533;'&#65533;&#65533;./&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.&#65533;X&#65533;Dt&#41484;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;YP&#65533;'&#65533;&#65533;</c&#65533;o&#65533;&#65533;v?&#65533;&#65533;&#65533;&#65533;*&#65533;&#65533;&#65533;b&#65533;&#65533;&#65533;&#65533;&#601;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;/&#65533;&#65533;&#1315;h5&#65533;&#1019;&#65533;Il&#65533;&#65533;w&#782;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14312: ignoring bad line starting with '&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;<&#65533;&#65533;t&#65533;&#65533;G&#65533;&#65533;x&#65533;&#65533;SJH&#65533;F&#65533;T&#65533;&#65533;&#65533;&#65533;p
                                                          &#65533;&#65533;`&#65533;PUAT&#65533;&#65533;&#65533;&#65533;y&#65533;I&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;w&#65533;&#65533;k
                i&#65533;&#65533;&#65533;&#65533;&#1683;&#65533;.&#65533;&#799;&#65533;&#65533;&#65533;C&#65533;|&#65533;&#65533;&#65533;i&#65533;>&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;D&#65533;S&#65533;&#65533;&#65533;Q>&#65533;p&#65533;&#885;&#65533;&#65533;ATA&#65533;x&#65533;&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>GC&#65533;&#65533;&#65533;&#2034;&#65533;&#65533;&#65533;~&#65533;&#65533;3&#65533;&#65533;/&#65533;&#65533;}g&#65533;&#990;Y&#65533;&#65533;vO7&#65533;&#65533;>B&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#471;.&#1660;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;w&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;oNi&#65533;M&#65533;&#65533;[V&#65533;7|&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;&#614;&#65533;i&#65533;&#65533;i&#65533;&#65533;(&#65533;&#65533;&#65533;O&#65533;&#65533;&#65533;v&#65533;&#65533;&#65533;ËM&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;.&#65533;&#65533;&#65533;0&#65533;b&#843;&#65533;k&#65533;&#65533;O&#65533;&#65533;&#65533;H)&#65533;&#65533;&#65533;x'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14313: ignoring bad line starting with 'Q&#1795;iO{&#65533;&#65533;@7&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14314: ignoring bad line starting with 'T&#65533;&#65533;&#65533;&#65533;#&#65533;r&#65533;&#65533;TFUVa&#65533;o&#65533;n~&#65533;?3&#65533;!"J&#805;&#65533;&#65533;&#65533;&#65533;&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;d&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;'&#65533;&#65533;&#65533;&#65533;{V&#65533;&#2027;&#65533;O&#1239;&#65533;&#65533;&#65533;/?&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;I&#65533;&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;&#1115;X&#1855;N&#28442;
&#65533;v&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;L&#65533;7&#65533;&#65533;e&#65533;}G&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;]&#65533;&#65533;&#65533;&#1717;]WOG^&#65533;_&#65533;o?&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;fUU9E&#65533;Y&#65533;UY&#65533;&#65533;&#65533;l&#65533;&#65533;+k2&#65533;&#65533;
   &#32374;&#65533;?&#65533;&#65533;'
WARNING: /etc/modprobe.d/alsa-driver-1.0.24.tar.bz2 line 14315: ignoring bad line starting with '/&#65533;&#65533;&#65533;'
cat: /proc/asound/modules: No such file or directory



```


Also tried following Ikjoel sound troubleshooting and ends up on something similar, at which point it directs me to [http://ubuntuforums.org/showthread.php?t=1681577]("http://ubuntuforums.org/showthread.php?t=1681577")
Should I follow it?


Thx again for helping me with this, i know I might be slow on replying but its only because I leave the computer at work.

---

