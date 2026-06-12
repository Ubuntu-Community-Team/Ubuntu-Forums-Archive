---
title: "Buy more efficient CPU vs. Underclock?"
date: 2011-01-25
forum: Mythbuntu
---

### Post by HarrisonFan on 2011-01-25
Hi,

I am planning on building my first Mythbuntu system and I would like to get your opinions on CPUs. I am building a dual backend / frontend machine and would want to be able to either record two strams at once or record one and watch on the other.

I was considering getting the [AMD Athlon 610e]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103899") because of the 45W power consumption.  Then I started wondering about underclocking a cheaper CPU (possibly the [AMD Athlon 640]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103871")).  

Opinions?  Would I get comparable power consumption and performance from a 640 underclocked?

One other thing to note is that I have not underclocked a CPU before (although it appears fairly easy).

Also, I guess I was thinking of going for a quad core but would I really notice any difference over a dual?

Thanks,
Zac

---

### Post by nickrout on 2011-01-25
A backend that simply records digital TV does not need a grunty cpu. A frontend that has a vdpau capable graphics card does not need a lot of grunt either. However transcoding and commercial detection do require grunt.

---

### Post by BicyclerBoy on 2011-01-25
It is not so much "more efficient vs underclock" as more efficient & under clock.
You are interested in power efficiency of the CPU.

By underclocking (& under-voltage) you end up with a better CPU but at a higher price.
The atom CPU is not great it is cheap low power so thermal design is easy.

The latest iMac mini is a good example of a solution (except the price).

Have not made any comparison of AMD CPUs as they seemed more the enemy than intel. Not sure if that is still the case.

With intel CPUs the i3 is more efficient than core2duo (L3 cache ?)
In real world tests the core2duo is >2x power efficiency of an atom 330.

The low power versions of sandybridge could be better than any AMD processor.
The Sandybridge looks to be 2x power efficiency of AMD Phenom X11.
Actually this holds true for current i3 & i5.

---

### Post by alien878 on 2011-01-26
If you are looking at power consumption, a few things to consider:

[LIST=1]
[*]For a myth box, it most cases it will be the power consumption and not the efficiency that is important.  Most efficiency reports take into account the horsepower of the CPU.  If you aren't using all the horsepower, you won't achieve that efficiency.
[*]It is the power consumption whole of the system and not the CPU that is important.  Often, the CPU is not the main consumer of power.
[*]Unless the system is on 7x24, the power consumption when the system is off is important.  Mythwelcome is a great power saver, especially if the system consumes almost nothing when it is off.
[/LIST]In summary, you probably want to get a watt meter and try things out.  My system (based on an ASUS AT3N7A-I) is about 35W total.  The disappointing part is the 7W is draws when off, but that might have been improved with a better PSU selection.

---

### Post by HarrisonFan on 2011-01-26
Thanks for your replies!

I was hoping to be able to use integrated Audio and Video then over HDMI to my TV.  I am also planning to use a WD Caviar Green 2TB drive for disk, and the Hauppauge 2250 dual tuner. I will hopefully also find an 80+ power supply.

How much grunt is recommended to be able to do transcoding and commercial detection for two streams? I want to make sure that whatever CPU I get would be able to handle this but would also not be a complete power hog.  I was planning on getting a quad core just because I figured it wouldn't hurt to have this extra multiprocessing bandwidth, but would I really see any difference between this and a dual?

I was planning on going with AMD because it has always seemed like you get more for your $ than with Intel, but I am not against using Intel if that would be a better fit. 

Thanks for your help!
Zac

---

### Post by cascade9 on 2011-01-27
Should be totally possible. An underclocked Athlon II X4 @ 610e speeds might lose a tiny bit of power vs the 610e (due to the locked mutliplier) but it probably would be much to worry about. 

The only problem with this idea is that you have the same issues as overclocking (possible unreliablity, having to figure out yourself what is stable or not, if something goes wrong you'll have to reset the BIOS and go back almost to square one, etc)

> **alien878 said:**
> If you are looking at power consumption, a few things to consider:

[LIST=1]
[*]For a myth box, it most cases it will be the power consumption and not the efficiency that is important. Most efficiency reports take into account the horsepower of the CPU. If you aren't using all the horsepower, you won't achieve that efficiency.
[*]It is the power consumption whole of the system and not the CPU that is important. Often, the CPU is not the main consumer of power.
[*]Unless the system is on 7x24, the power consumption when the system is off is important. Mythwelcome is a great power saver, especially if the system consumes almost nothing when it is off.
[/LIST]
In summary, you probably want to get a watt meter and try things out. My system (based on an ASUS AT3N7A-I) is about 35W total. The disappointing part is the 7W is draws when off, but that might have been improved with a better PSU selection.

1- True.
2- Again, true, but anybody using a 'gamers' video card for a HTPC is either building a dual-purpose box, or using the parts they have already, or needs a headcheck.
3- Turn of the power? You dont need to leave computers on standby. I switch of my computer totally every night (or morning with my sleeping hours) 

> **nickrout said:**
> A backend that simply records digital TV does not need a grunty cpu. A frontend that has a vdpau capable graphics card does not need a lot of grunt either. However transcoding and commercial detection do require grunt.

+1. 

I dont know how much power you need for commercial detection, as long as its not to bad you could possibly get away with far less CPU power than a 610e. 

> **BicyclerBoy said:**
> Have not made any comparison of AMD CPUs as they seemed more the enemy than intel. Not sure if that is still the case.

I was temped to make a far bigger reply to this, but that would just complicate things. 

But this one I can let go......how the heck do you figure that AMD is more of an 'enemy' than Intel? o.O

---

### Post by alien878 on 2011-01-27
> **cascade9 said:**
> 3- Turn of the power? You dont need to leave computers on standby. I switch of my computer totally every night (or morning with my sleeping hours)The computer is off.  However, the PSU is still plugged in.  I could unplug the computer, but then ACPI wakeup wouldn't work and nothing would record (i.e. mythwelcome).

What is interesting is that the efficiency rating of a PSU is almost meaningless for my type of setup because it measures the efficiency under load.  My box is on maybe 2h per day.  That's 70Wh.  However, it is off 22h per day.  That's 154Wh.  The biggest electricity cost is when the computer is "off".

---

### Post by cascade9 on 2011-01-27
> **alien878 said:**
> The computer is off.  However, the PSU is still plugged in.  I could unplug the computer, but then ACPI wakeup wouldn't work and nothing would record (i.e. mythwelcome).

Depends on what you call 'off'. I dont count standby as off myself. Not that you've got the option to turn it off if you want it to wake up. 

> **alien878 said:**
> What is interesting is that the efficiency rating of a PSU is almost meaningless for my type of setup because it measures the efficiency under load.  My box is on maybe 2h per day.  That's 70Wh.  However, it is off 22h per day.  That's 154Wh.  The biggest electricity cost is when the computer is "off".

The efficiency rating rating of  a PSU is in the 'on' state, under some load (normally the efficiency drops dramatically under 25-35%of the total max output). All the manufacturers list the highest efficiency level achived, and most people will never get it. 

There is a reference to "power supplies designed for low stanby power" in the ATX power supply design guide- 

[http://www.formfactors.org/developer/specs/ATX12V_PSDG_2_2_public_br2.pdf](http://www.formfactors.org/developer/specs/ATX12V_PSDG_2_2_public_br2.pdf)

Nobody I've seen lists standby power requirements.....which is a pity, as this problem is serious as far as I'm concerned. 

There is EU Eco-label and GEETA which does specify standby power requirements. In off mode, EU Eco-label demands equal to 5watts or less, GEETA just less than 5watts. There is also- 

[http://www1.eere.energy.gov/femp/technologies/buying_low_standby.html](http://www1.eere.energy.gov/femp/technologies/buying_low_standby.html)

BTW, if you are using  a wall plug monitor to get your standby power draw, AFAIK most of them are not that accurate, and at very low power draw they are even less accurate.

---

### Post by LowSky on 2011-01-27
If your going to complain about how much it cost sto have the PC just sit there turned off maybe you need to ask yourself, "Do I really need a HTPC?" If you already have another desktop in the house why not have it do double duty? Save money buying parts that you can put toward your electric bill. My desktop acts as my main PC, mythtv backend, mythtv frontend, UPnP media server, and print server.

---

### Post by alien878 on 2011-01-27
Hmmmm.... Doing a bit of reading it seems that PSU standby (not to be confused with computer standby) typically draws .5 to 3W.  7W is closer to what one would expect from a no-load scenario.

I'm going to have to look a bit closer.  Maybe the PSU isn't dropping into standby like it should.

---

### Post by cchhrriiss121212 on 2011-01-27
I have an Athlon II 245 running stable at stock speed with a lowered voltage of 1.15v, you can get it even lower if you reduce the speed. With this CPU you could afford a dedicated GPU like a low power gt210 that would enable vdpau output. Just something to think about.

---

### Post by HarrisonFan on 2011-01-27
cchhrriiss121212, does your Athlon II 245 still have enough power to transcode and do commercial detection? Do you figure it would for two streams simultaneously?

From everyone else's posts it seems like it may be more worthwhile to spend the extra $ for a better PS and not really worry much about the CPU power draw inder load. I'll be sure to look for a EU Eco-label or GEETA labeled PS to try to save power when off. Thanks for the info!

Thanks,
Zac

---

### Post by cascade9 on 2011-01-27
> **alien878 said:**
> Hmmmm.... Doing a bit of reading it seems that PSU standby (not to be confused with computer standby) typically draws .5 to 3W. 7W is closer to what one would expect from a no-load scenario.

I'm going to have to look a bit closer.  Maybe the PSU isn't dropping into standby like it should.

When I said 'standby' I didnt mean what some call standby (ie, computer keeps the data in RAM butdrops the power to everything else it can, more normally known as 'sleep mode'). They should never have called that mode 'standby' because its to easy to confuse with standby for other electronics. 

BTW, its possible for USB devices to remain drawing power in standby. That could be causing extra power draw as well. 

> **HarrisonFan said:**
> cchhrriiss121212, does your Athlon II 245 still have enough power to transcode and do commercial detection? Do you figure it would for two streams simultaneously?

From everyone else's posts it seems like it may be more worthwhile to spend the extra $ for a better PS and not really worry much about the CPU power draw inder load. I'll be sure to look for a EU Eco-label or GEETA labeled PS to try to save power when off. Thanks for the info!

Thanks,
Zac

I havent seen any power supplies with an EU Eco-label or a GEETA label. I have seen 'blue angel' (RAZ-UZ) on occasion, which is another power consumption/energy saving specification.

By all means, get a better power supply. Dont forget that the bigger the power supply, the more likely that you will be in the 'bad' part of the effiency graph. 

Also, there is one other reason why underclocking (or getting a low consumption CPU) is a good idea for a HTPC- noise. The more power draw = the more heat to dump, and the more heat, the faster the CPU fan will spin. 

That is one nice thig gabout the XXXe series AMD CPUs is that not onle is the total heat output lower, the idle heat output is lower as well. Due to lower 'low' voltage setings ;)

---

### Post by cchhrriiss121212 on 2011-01-27
> cchhrriiss121212, does your Athlon II 245 still have enough power to transcode and do commercial detection? Do you figure it would for two streams simultaneously?
I don't use my machine for this stuff, but in terms of specs the 245 is similar to the 640 while being significantly cheaper and draws less power. Cascade has said the 640 should have sufficient power so it seems like a good choice to me.

But maybe some-one else can explain how much practical difference those 2 extra cores will make.

---

### Post by cascade9 on 2011-01-27
> **cchhrriiss121212 said:**
> I don't use my machine for this stuff, but in terms of specs the 245 is similar to the 640 while being significantly cheaper and draws less power. Cascade has said the 640 should have sufficient power so it seems like a good choice to me.

But maybe some-one else can explain how much practical difference those 2 extra cores will make.

I dont recall saying that, but if I did, I agree with myself :lolflag: 

I did find this- 

[http://ubuntuforums.org/showthread.php?t=613873](http://ubuntuforums.org/showthread.php?t=613873)

Long story short, for those that dont like following links- 

> ZY15: Base processor and speed: Intel Pentium (R) III / 1 GHz Processor,133 MHz FSB
Chipset: Intel 810E
RAM:  128 MB RAM PC100 
Video Memory:  11 MB shared, integrated graphics, not upgradeable 

uopjohnson:You probably won't be able to transcode and commercial detection is going to take forever, but it will run.  

If commercial detection will even run on a P3/1GHz 128MB setup, even a sempron with any decent amount of RAM should do the job. AAthon II dualcore should be more than enough IMO. 

But I'm not expert, maybe someone who uses commercial detection on a myth box has a better idea of the CPU power/time to run commercial detection realationship.

---

### Post by cchhrriiss121212 on 2011-01-27
> **cascade9 said:**
> I dont recall saying that, but if I did, I agree with myself 
Heh, must be my clairvoyance kicking in. :P
> That is one nice thing about the XXXe series AMD CPUs is that not only is the total heat output lower, the idle heat output is lower as well. Due to lower 'low' voltage settings :wink:A good point, my 245 has dropped around 15 degrees C from undervolting. The xxxe series are priced a bit higher due to their rarity, so pick up the regular version and undervolt, in most cases they are the exact same CPU.

---

### Post by HarrisonFan on 2011-01-27
> **cchhrriiss121212 said:**
> Heh, must be my clairvoyance kicking in. :P
A good point, my 245 has dropped around 15 degrees C from undervolting. The xxxe series are priced a bit higher due to their rarity, so pick up the regular version and undervolt, in most cases they are the exact same CPU.

Thanks for the advice!

Is there a general consensus about Dual vs Tri vs Quad cores? Do you think I will really see any difference with the extra 2 cores if I am using a VDPAU capable integrated video mb?

---

### Post by cascade9 on 2011-01-27
> **cchhrriiss121212 said:**
> Heh, must be my clairvoyance kicking in. :razz:

While your hot.....what is next weeks lottery numbers? :lolflag: 

> **HarrisonFan said:**
> Thanks for the advice!

Is there a general consensus about Dual vs Tri vs Quad cores? Do you think I will really see any difference with the extra 2 cores if I am using a VDPAU capable integrated video mb?

For video watching? You'll never see the difference. A tri or quad core will do commercial decection faster, but how much you would need or want that I dont know.

---

### Post by HarrisonFan on 2011-01-27
> **cascade9 said:**
> 
For video watching? You'll never see the difference. A tri or quad core will do commercial decection faster, but how much you would need or want that I dont know.

Thanks!  I may just get a Tri core that is on sale and underclock it to get a little better power savings.  Once I figure out what I want for the system I would like to post the specs and get peoples opinions.  Would that be better as a seperate thread or should I do that here? (I haven't been very active at this forum so I don't know the protocol)

Thanks Again!

---

### Post by cascade9 on 2011-01-27
I'd consider doing both. 

The more pages in a thread, the less people will read it (IMO anyway). So starting a new thread (probably in 'hardware & laptops') should get a few people who might not bother reading to page 3 on this thread. You'll also get people who wont really look a overclocking/underclockign threads. 

Posting the specs here as well just increases your chances of getting a decent reply. ;)

---

