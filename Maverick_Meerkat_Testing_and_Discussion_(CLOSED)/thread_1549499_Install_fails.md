---
title: "Install fails"
date: 2010-08-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Nesaskewatch on 2010-08-09
G'day!

I have been trying to install from a live dvd, but it hangs near the end with "Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm Line 39, <> Line 158."  Exactly as shown.  I have tried three times with the same result.  Is my dvd corrupt?  I guess it wouldn't hurt to try and burn another disc, but I am curious as to what is failing.  Is that a code error?  (Perl5)  

Here is a copy of the file in question

```
#!/usr/bin/perl -w
# This file was preprocessed, do not edit!


package Debconf::DbDriver::Cache;
use strict;
use Debconf::Log qw{:all};
use base 'Debconf::DbDriver';


use fields qw(cache dirty);


sub iterator {
	my $this=shift;
	my $subiterator=shift;

	my @items=keys %{$this->{cache}};
	my $iterator=Debconf::Iterator->new(callback => sub {
		while (my $item = pop @items) {
			next unless defined $this->{cache}->{$item};
			return $item;
		}
		return unless $subiterator;
		my $ret;
		do {
			$ret=$subiterator->iterate;
		} while defined $ret and exists $this->{cache}->{$ret};
		return $ret;
	});
	return $iterator;
}


sub exists {
	my $this=shift;
	my $item=shift;

	return $this->{cache}->{$item}
		if exists $this->{cache}->{$item};
	return 0;
}


sub init {
	my $this=shift;

	$this->{cache} = {} unless exists $this->{cache};
}


sub cacheadd {
	my $this=shift;
	my $item=shift;
	my $entry=shift;

	return if exists $this->{cache}->{$item};

	$this->{cache}->{$item}=$entry;
	$this->{dirty}->{$item}=0;
}


sub cachedata {
	my $this=shift;
	my $item=shift;
	
	return $this->{cache}->{$item};
}


sub cached {
	my $this=shift;
	my $item=shift;

	unless (exists $this->{cache}->{$item}) {
		debug "db $this->{name}" => "cache miss on $item";
		$this->load($item);
	}
	return $this->{cache}->{$item};
}


sub shutdown {
	my $this=shift;
	
	return if $this->{readonly};

	my $ret=1;
	foreach my $item (keys %{$this->{cache}}) {
		if (not defined $this->{cache}->{$item}) {
			$ret=undef unless defined $this->remove($item);
			delete $this->{cache}->{$item};
		}
		elsif ($this->{dirty}->{$item}) {
			$ret=undef unless defined $this->save($item, $this->{cache}->{$item});
			$this->{dirty}->{$item}=0;
		}
	}
	return $ret;
}


sub addowner {
	my $this=shift;
	my $item=shift;
	my $owner=shift;
	my $type=shift;

	return if $this->{readonly};
	$this->cached($item);

	if (! defined $this->{cache}->{$item}) {
		return if ! $this->accept($item, $type);
		debug "db $this->{name}" => "creating in-cache $item";
		$this->{cache}->{$item}={
			owners => {},
			fields => {},
			variables => {},
			flags => {},
		}
	}

	if (! exists $this->{cache}->{$item}->{owners}->{$owner}) {
		$this->{cache}->{$item}->{owners}->{$owner}=1;
		$this->{dirty}->{$item}=1;
	}
	return $owner;
}


sub removeowner {
	my $this=shift;
	my $item=shift;
	my $owner=shift;

	return if $this->{readonly};
	return unless $this->cached($item);

	if (exists $this->{cache}->{$item}->{owners}->{$owner}) {
		delete $this->{cache}->{$item}->{owners}->{$owner};
		$this->{dirty}->{$item}=1;
	}
	unless (keys %{$this->{cache}->{$item}->{owners}}) {
		$this->{cache}->{$item}=undef;
		$this->{dirty}->{$item}=1;
	}
	return $owner;
}


sub owners {
	my $this=shift;
	my $item=shift;

	return unless $this->cached($item);
	return keys %{$this->{cache}->{$item}->{owners}};
}


sub getfield {
	my $this=shift;
	my $item=shift;
	my $field=shift;
	
	return unless $this->cached($item);
	return $this->{cache}->{$item}->{fields}->{$field};
}


sub setfield {
	my $this=shift;
	my $item=shift;
	my $field=shift;
	my $value=shift;

	return if $this->{readonly};
	return unless $this->cached($item);
	$this->{dirty}->{$item}=1;
	return $this->{cache}->{$item}->{fields}->{$field} = $value;	
}


sub removefield {
	my $this=shift;
	my $item=shift;
	my $field=shift;

	return if $this->{readonly};
	return unless $this->cached($item);
	$this->{dirty}->{$item}=1;
	return delete $this->{cache}->{$item}->{fields}->{$field};
}


sub fields {
	my $this=shift;
	my $item=shift;
	
	return unless $this->cached($item);
	return keys %{$this->{cache}->{$item}->{fields}};
}


sub getflag {
	my $this=shift;
	my $item=shift;
	my $flag=shift;
	
	return unless $this->cached($item);
	return $this->{cache}->{$item}->{flags}->{$flag}
		if exists $this->{cache}->{$item}->{flags}->{$flag};
	return 'false';
}


sub setflag {
	my $this=shift;
	my $item=shift;
	my $flag=shift;
	my $value=shift;

	return if $this->{readonly};
	return unless $this->cached($item);
	$this->{dirty}->{$item}=1;
	return $this->{cache}->{$item}->{flags}->{$flag} = $value;
}


sub flags {
	my $this=shift;
	my $item=shift;

	return unless $this->cached($item);
	return keys %{$this->{cache}->{$item}->{flags}};
}


sub getvariable {
	my $this=shift;
	my $item=shift;
	my $variable=shift;

	return unless $this->cached($item);
	return $this->{cache}->{$item}->{variables}->{$variable};
}


sub setvariable {
	my $this=shift;
	my $item=shift;
	my $variable=shift;
	my $value=shift;

	return if $this->{readonly};
	return unless $this->cached($item);
	$this->{dirty}->{$item}=1;
	return $this->{cache}->{$item}->{variables}->{$variable} = $value;
}


sub variables {
	my $this=shift;
	my $item=shift;

	return unless $this->cached($item);
	return keys %{$this->{cache}->{$item}->{variables}};
}


1
```

And now, for $500,000.00 and a brand new car, can you spot the problem?

Like I said, just curious.  But should I burn another disc?  Or, should I wait for another build?  This was the amd64 dvd downloaded on Saturday from the daily build site.

BTW  I am using the live dvd right now.  Works fine...

---

### Post by krash1220 on 2010-08-09
No, because I'm getting a similar error message. For the last 3 or 4 daily builds that I've put on USB drive install stops at:

-retrieving file 18 of 18

Ubiquity 2.3.4
** Message: pygobject_register_sinkfunc is deprecated (GtkWindow)
** Message: pygobject_register_sinkfunc is deprecated (GtkInvisible)
** Message: pygobject_register_sinkfunc is deprecated (GtkObject)
exception: <urlopen error [Errno 110] connection times out>
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template/Cache.pm line 39,<> line 200.

So today I burned it to CD and I get the same error but with a different line. /usr/share/perl5/Debconf/DbDriver/Cache.pm Line 39, <> Line 158.

---

### Post by VMC on 2010-08-09
I think several people are getting the apparent error in the 5-line output display. I had a rather bazaar method to go beyond that error message and get mine installed.

What are the specs of your computer?

---

### Post by krash1220 on 2010-08-09
Mines a Gateway Laptop 

AMD Athlon II P320 Dual-Core Processor 
4 gigs ram

---

### Post by ronacc on 2010-08-09
yeah they munged up ubiquity good this time , see also this thread .
[ http://ubuntuforums.org/showthread.php?t=1548416 ]( http://ubuntuforums.org/showthread.php?t=1548416 )

---

### Post by Nesaskewatch on 2010-08-09
> **VMC said:**
> 
What are the specs of your computer?

Sorry bout that.  Toshiba Satelite L500-00U.  Intel dual core T4300.  3 gigs ram.

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

I had the same preamble as Krash1220 as well.  But it popped up right away during install, and didn't seem to affect anything until the lines I posted came up at "retrieving file 22 of 22" then it hangs.  

Cheers!

---

### Post by Nesaskewatch on 2010-08-09
> **ronacc said:**
> yeah they munged up ubiquity good this time , see also this thread .
[ http://ubuntuforums.org/showthread.php?t=1548416 ]( http://ubuntuforums.org/showthread.php?t=1548416 )

Ya, I saw that the other day when I was searching for other issues like mine.  Figured I was lucky I was installing to my testing partition only.  I guess I'll hold off for a bit before wasting another dvd.  I should pickup an 8 gig thumb drive for this though...

Cheers!

---

### Post by krash1220 on 2010-08-09
I would definitely be interested in a workaround if there is one.

---

### Post by ronacc on 2010-08-09
I think in this case the workaround is to wait for the devs to straighten it out .

---

### Post by VMC on 2010-08-10
> **krash1220 said:**
> I would definitely be interested in a workaround if there is one.
I found a hack around that works, but I'm sure tomorrow will bring more issues. I've been waiting it out for the past several ISO's hoping that it was a kernel issue. Worried that it was nVidia only I pursued and found out from reading several topics that its not just an nVidia problem.

For the OP, Nesaskewatch, when it stops issue Ctrl+Alt+F1 then go to the ```
/var/log
``` and look at some outputs - syslog, kernlog, and Xorg.0.log. Look also inside ```
/var/log/installer/dm
``` file.
They all tell a story.

---

### Post by Nesaskewatch on 2010-08-10
> **VMC said:**
> For the OP, Nesaskewatch, when it stops issue Ctrl+Alt+F1 then go to the ```
/var/log
``` and look at some outputs - syslog, kernlog, and Xorg.0.log. Look also inside ```
/var/log/installer/dm
``` file.
They all tell a story.

This is a great way to learn a new language!  I will follow [this]("http://ubuntuforums.org/showthread.php?t=1548416") from here out.  That's where the action is.  Thanks for the advice!

Cheers!

---

