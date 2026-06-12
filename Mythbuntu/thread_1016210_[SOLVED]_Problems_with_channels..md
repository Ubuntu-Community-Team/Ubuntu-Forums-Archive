---
title: "[SOLVED] Problems with channels."
date: 2008-12-19
forum: Mythbuntu
---

### Post by whirl on 2008-12-19
Hey!

First of all I have ubuntu 8.10 x64 with two of Terratec Cinergy C PCI HD ([http://www.terratec.net/en/products/Cinergy_C_PCI_HD_1976.html]("Cinergy C PCI HD")) cards and Ive got the drivers with the help from [http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C") with mythbuntu installed from the ubuntu repos.

The cards should be working well because I can scan channels with mythbuntu and when I try to watch them I get the info of what is on at the channel. But I cant get any picture at all because the signal strenght goes constantly up and down from 4% to 50% but never over that. It even says to me that you shouldve got a lock already and so on. And the second one is that Im afraid that some of scanned channels arent properly scanned or something like that (excuse my ignorance) because on some channels I dont even get the info of whats on at the moment.

So these are the problems: Signal strenght going up and down with no picture and possible problem with scanned channels that dont even give any info of whats on at the channels.

Ive tried googling these issues and found probable solvers but I just cant get these work. 
First one is for this signal strenght and black screen issue (or atleast I think it has something to do with my problem) and you can find it here: [http://www.mythtv.org/wiki/index.php/Channel_tuning_broken_with_DVB-C#modified_mythic.pl_solution]("http://www.mythtv.org/wiki/index.php/Channel_tuning_broken_with_DVB-C#modified_mythic.pl_solution"). Ive tried to run this mythic.pl but this is what I get:
```
vemi@digiboksi:~$ perl mythic.pl
Can't locate enum.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at mythic.pl line 7.
BEGIN failed--compilation aborted at mythic.pl line 7.
vemi@digiboksi:~$ 

```
Whats wrong with the script and is this even the right way to go with this issue?

The second one might have something to with my cable provider and I found a finnish site who has installed mythtv and explains whats wrong with our cable producer (those who understand it [http://www.warrantyvoid.info/2007/04/mythtv-tampereen-kaapeliverkkoon/]("http://www.warrantyvoid.info/2007/04/mythtv-tampereen-kaapeliverkkoon/")) basicly he says that some of the channel bundles (bundles? bunches? hope you understand what I mean) come with network id 0 and I need to run this [http://svn.mythtv.org/trac/attachment/ticket/2528/eit_fix.diff]("http://svn.mythtv.org/trac/attachment/ticket/2528/eit_fix.diff") to get things rolling again. But here we come to the limit of my knowledge. Where to do I donwload this patch to be able to run it successfully? Because the guide says that I should do it like this:
```
# cd /usr/src
# wget http://svn.mythtv.org/trac/attachment/ticket/2528/eit_fix.diff
# patch -p0 < eit_fix.diff
```
I cant see folders with something to do with mythtv in /usr/src and I cant see any logic putting it up there. So what next?

Heres what Ive gatherd of my problems this far and rely on others to help me pass these problems so that I could watch tv with my brand new box. If Ive left something out please do ask and Ill provide it here. Thanks in advance!

-------------------------------------------------------------
SOLVED

Maybe it had something to do with x64 cause I tried installing mythbuntu 8.10 i386 from live-cd and its all working smoothly. Maybe the mantis driver from [www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C]("www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C") doesnt work with x64.

Thanks again and hope this helps someone o/

---

