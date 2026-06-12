---
title: "NIS Authentication with Autofs"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by uniman on 2010-09-06
Hi Guys
Having searched through the forums, I cannot find an answer to the problem, lot of talk but no answer.
I am using Ubuntu 10.04 as client and SLES9SP3 as server. The desktop can ping the server, ypcat produces the correct results. I can manually mount the home drive. I have the various protocols loaded, nis, nfs-common, autofs, portmap. I have used a document from the Ubuntu wiki to configure the client which does not mention or appear to use nsswitch or the auto.master/home files.
If somebody could point in the direction of a decent how to for nis and Ubuntu 10.04 that would be great.

---

### Post by haihovu on 2010-11-16
I just set this up last week and kept a journal of my experience here it is:

**[COLOR=#000000][FONT=Arial][B]AutoFS with NIS**[/FONT][/COLOR][/B]

[COLOR=#000000][FONT=Arial]Normally  autofs gets its mapping data from local files auto.master, ... However,  autofs can use mapping info from the NIS/YP database. Though there is  not a lot of clear information on how to program up autofs mapping  information with NIS out on the web, I have inferred from here [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_http://penguin.triumf.ca/recipes/nis-auto/_[/FONT][/COLOR]]("http://penguin.triumf.ca/recipes/nis-auto/")[COLOR=#000000][FONT=Arial]  that this may be found in the makefile. Sure enough NIS default  makefile, /var/yp/Makefile contains enough instruction on how to build  your own autofs map in the NIS database, though normally commented out.  In this scenario, NIS runs on the server(s) and provides map data to  autofs running on the clients.[/FONT][/COLOR]
**[COLOR=#000000][FONT=Arial][B]NIS Server**[/FONT][/COLOR][/B]

[COLOR=#000000][FONT=Arial]To implement your own custom autofs map data via NIS simply edit /var/yp/Makefile, on the NIS server, as follows:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]Locate  the definition for AUTO_MASTER use it as a template to add your own map  entry such as AUTO_HOME, ... I’d avoid using the autofs map files from  /etc since it may be used for the local autofs (of the server), I made a  copy of these files to some other local directory and pointed the  Makefile there. Example:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]AUTO_MASTER   = /autofs_src/auto.master[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]AUTO_HOME   = /autofs_src/auto.home[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]...[/FONT][/COLOR]
[/LIST]
[/LIST]

[LIST]
[*][COLOR=#000000][FONT=Arial]Locate the definition of the macro ALL, and append the rules for making your autofs map entries to ALL like so:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]ALL += auto.master auto.home ...[/FONT][/COLOR]
[/LIST]
[*][COLOR=#000000][FONT=Arial]Now locate the rule for making auto.master and use it as a template for creating your custom map entries, something like this:[/FONT][/COLOR]
[/LIST]

[LIST]
[LIST]
[*][COLOR=#000000][FONT=Arial]auto.home: $(AUTO_HOME) $(YPDIR)/Makefile[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]        @echo "Updating $@..."[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]        -@sed -e "/^#/d" -e s/#.*$$// $(AUTO_HOME) | $(DBLOAD) \[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]                -i $(AUTO_HOME) -o $(YPMAPDIR)/$@ - $@[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]        -@$(NOPUSH) || $(YPPUSH) -d $(DOMAIN) $@[/FONT][/COLOR]
[/LIST]
[/LIST]

[LIST]
[*][COLOR=#000000][FONT=Arial]That’s it, rebuild NIS database, restart nis, and your server should be ready to serve up autofs map data to clients.[/FONT][/COLOR]
[/LIST]

**[COLOR=#000000][FONT=Arial][B]Autofs Client**[/FONT][/COLOR][/B]

[COLOR=#000000][FONT=Arial]On the clients side, you have some flexibility as to how to configure autofs to get its mapping information:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]From local file[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]From NIS database[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]From both of the above[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]This decision is made inside /etc/nsswitch.conf by adding the following:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]# Automount data comes from NIS database alone[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]automount: nis[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]OR[/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]# Automount data comes from local files (/etc/auto.master, ...) alone[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]automount: files[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]OR[/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]# Automount data comes from local files first if found, and then from NIS database.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]automount: files nis[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In  the cases where the autofs mapping data comes from local files there is  nothing new to add here, there are ample of available documentation  describing how to do this already.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Where  the autofs mapping data is provided by NIS database alone, make sure  you edit /etc/nssswitch.conf as described above, and optionally remove  all autofs mapping files under /etc, including /etc/auto.master (or  simply renaming them) just to be sure. Try executing ypcat auto.master  and some other autofs map entries that you created in the NIS server to  see if it show what you’d expect. Example:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]hai@server2:~$ ypcat auto.master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]auto.backup[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]auto.home[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]auto.public[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]auto.share[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]hai@server2:~$ ypcat auto.home[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]server:/home/&[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If  you use a combination of local files plus NIS database, first make sure  that nssswitch.conf is set up as described previously, typically you’d  have your own /etc/auto.master (it wouldn’t make much sense otherwise).  Then in auto.master refer to the map entries from local file as their  full path file names, and map entries from NIS database as simple names  without the file path, as illustrated the in example below:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# This uses mapping data from the NIS database[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/home auto.home[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# This uses mapping data from the local file[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/share /etc/auto.share[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
Good luck,

---

