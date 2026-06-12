---
title: "Channel Scan Issues and w_scan"
date: 2009-02-08
forum: Mythbuntu
---

### Post by roundhay on 2009-02-08
I am having problems with the channel scanning in mythtv (well documented issues for many DVB-C users.

To help me check that the patches I am going to apply are working I would like to be able to check the info in myth. 

The data I get from (dvb)scan does n ot give the net id or transport id, w_scan does output this info but it is not configured to run on my symbol rate 6952000, does anyone know how I can compile a version of w_scan which would scan this SR?

Just found this link.....fingers crossed...

[https://lists.ubuntu.com/archives/kubuntu-bugs/2008-May/046952.html](https://lists.ubuntu.com/archives/kubuntu-bugs/2008-May/046952.html)

---

### Post by roundhay on 2009-02-12
Not only do I need to update the symbol rate in w_scan but I also need to change the frequencies it scans, any ideas?

I cannot get my channels to lock and the correct info from a scan to be stored in the mythfilldatabase. I think I am suffering from the problem discussed in the following trac thread:

[http://svn.mythtv.org/trac/ticket/3640](http://svn.mythtv.org/trac/ticket/3640)

Does anyone know how to apply the patch dvb_broken_nit_providers1.diff taht is discussed in this thread?

It seems like this is a common problem with DVB-C in some countries...

---

### Post by wirbel2 on 2009-02-14
I guess you use a tt premium c2300 dvb-c? If so, you are not suffering a software problem, but a hardware problem instead.

---

### Post by roundhay on 2009-02-14
No I'm using a TT C1501.

I definitely don't think it is a hardware problem.

I can time into a single frequency and view all of the channels on this frequency perfectly.

I just need to find out how to be able to tune to more than one frequency.

From the info I have been able to find I think my issues are due to the channel scanning function of mythtv, it just does not work for me.

---

### Post by wirbel2 on 2009-02-15
Also a driver known to have problems, but only on qam256..

The symbolrate of 6952 is quite unusual. Usual values are..
6900
6875
6950
in rar cases: 6111, 6250, 6790

To what combination of

- frequency
- symbolrate
- modulation (qam64, qam256)

do you have to tune to get reception and what comes out from channel scanner - either w_scan or dvbscan?

---

### Post by roundhay on 2009-02-15
The settings for my cable provider and location are:

sr =6952000
main frequency 666750000
QAM = 64
The frequencies are at 8000000 intervals, bandwidth = 8Mhz

I can tune to channels using (dvb)scan and can generate channels.conf files

There may be a driver error that stop the card retuning to a new frequency? I have not read about this anywhere but it would be one explanation of the problem I am having.

I have been running a few dvbsnoop commands after tuning to a channel using czap but I'm not sure how to interpret the data?

myth is a great program but there seem to be a lot of fundamental issues like channel scanning that need to be sorted.

---

### Post by wirbel2 on 2009-02-15
well - that frequency is also absolutely seldom. Usually is something like
(306 + N * 8) MHz with N = 21 .. 69, so 666MHz would be the nearest value.

Does give the (dvb)scan result give also that frequency 666.750MHz that you can successfully tune? Or may you post the scan result here?

---

### Post by wirbel2 on 2009-02-18
Your provider seems to use values where probably all automatic scan tools will fail. Therefore i suggest to use some home-made shell script in conjunction with classic (dvb)scan. Patching w_scan is also quite simple (changing only a few lines), but this would lead to the very same result as dvbscan here - but if you'r interested i would tell you where and how.

*usually* (but not in all cases) it's sufficient to tune successfully one frequnecy/transponder to find all the other channels via network information table (NIT), but for such a broken dvb network this might not work as well.

The following shell script will produce one file in your home directory and use that for scanning with dvbscan.

```

#/bin/bash

echo "# broken cable provider, use manual scanning." > ~/tuning_data
echo "# freq sr fec mod" >> ~/tuning_data

# c/c++ type loop inside bash shell here.
# Double parentheses, and "channel" with no "$".

for ((channel=21; channel <= 90 ; channel++))  
do
  let 'frequency = channel * 8000000 + 138750000'
  echo "C $frequency 6952 NONE QAM64" >> ~/tuning_data
  echo "C $frequency 6952 NONE QAM256" >> ~/tuning_data
done

scan -a0 -n ~/tuning_data >> ~/channels.conf

```

---

### Post by aaron@roydhouse.com on 2009-03-28
I was having trouble tuning in all the DVB-T channels for the Kings Cross area in Sydney, Australia. The files that came with (dvb)scan seemed quite out of date.

I found the DVB-T channel plan for Australia here:
[INDENT][http://www.dtvforum.info/lofiversion/index.php/t19148.html](http://www.dtvforum.info/lofiversion/index.php/t19148.html)
[/INDENT]
I found what appears to be up to date local channel info for Australia here:
[INDENT][http://vk3khb.gak.net.au/tv_lists/](http://vk3khb.gak.net.au/tv_lists/)[/INDENT]
I used the New South Wales, Australia info:
[INDENT][http://vk3khb.gak.net.au/tv_lists/nsw_tv_list.html](http://vk3khb.gak.net.au/tv_lists/nsw_tv_list.html)[/INDENT]

And I adapted (poorly) the script in this thread to generate all frequencies and variants that seem possible for Australia. This allowed a 'brute force' scan to generate a channels file.

After the brute force scan I made my own local tuning file for my area, and ran a scan again.

Attached are the:
[LIST]
[*]channel plan information
[*]script to generate a tuning file
[*]tuning file for Australia, for use with (dvb)scan
[*]hand-prepped tuning file for Kings Cross, Sydney, Australia, for use with (dvb)scan
[*]channels file for Kings Cross, Sydney, Australia for use with me-tv, gstreamer, xine, Totem, Kafeine, mplayer, or whatever
[/LIST]

The tuning and channels files worked well for me with me-tv. All the channels were found and the video and audio worked on all of them. With Totem the video works but not the audio, so I assume an audio codec is missing there.

For anyone's interest, this testing was with a Pinnacle Nano (73e) USB stick on a Lenovo X301 runing 64-bit (amd64) Ubuntu 8.10 (Intrepid). I used both the stock 0.5 me-tv and the 0.7 version from Launch-pad.

A couple of the channels weren't perfect and stuttered and re-buffered every couple of seconds for me. Might be a bandwidth issue or just poor reception, not sure. The ones I had trouble with were: 'SBS Radio 1', 'SBS Radio 2', '7 HD', 'ONE HD'. The rest all work great include SBS HD and ABC HDTV.

Are there any possible combinations for Australian DVB-T that I have missed?

Can I make more of the options automatic, i.e. where (dvb)scan can work them out?

Note that the script just tests for guards of 1/8 and 1/16. I found that the 'Digital 44' channels used a guard of 1/32. Why do none of the TV networks publish these details on their website?? :confused:

Aaron.

---

### Post by dibuntux on 2009-04-01
This is very interesting. I tried both your script and the wirbel2 one. I get a syntax error for the loop in both (line 13 in yours and line 9 in wirbel2).
Also your script lack the scan command... I'm confuse on the usage. Can you be more detailed?
Thanks

---

### Post by aaron@roydhouse.com on 2009-04-01
> **dibuntux said:**
> This is very interesting. I tried both your script and the wirbel2 one. I get a syntax error for the loop in both (line 13 in yours and line 9 in wirbel2).
Also your script lack the scan command... I'm confuse on the usage. Can you be more detailed?
Thanks

No, you'll have to type 'scan' yourself :-) 

It is a two-step process:
1) The script generates the possible frequencies
2) scan tries all those frequencies and generates a list of any channels it find

Regards the syntax error, check you actually have bash and that it is up to date.

Aaron.

---

