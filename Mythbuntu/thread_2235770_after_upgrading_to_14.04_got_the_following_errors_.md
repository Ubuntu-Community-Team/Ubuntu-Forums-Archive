---
title: "after upgrading to 14.04 got the following errors when reinstalling mythtv"
date: 2014-07-22
forum: Mythbuntu
---

### Post by phillip9 on 2014-07-22
hi got the following after upgrading any one know what might be wrong at all any help would be greatly appreciated thanks

[FONT=arial]Couldn't find any package whose name or description matched "full-upgrade"[/FONT]
[FONT=arial]The following partially installed packages will be configured:[/FONT]
[FONT=arial]  mythtv mythtv-database [/FONT]
[FONT=arial]No packages will be installed, upgraded, or removed.[/FONT]
[FONT=arial]0 packages upgraded, 0 newly installed, 0 to remove and 0 not to upgrade.[/FONT]
[FONT=arial]Need to get 0 B of archives. After unpacking 0 B will be used.[/FONT]
[FONT=arial]Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...[/FONT]
[FONT=arial]ERROR 1046 (3D000) at line 22: No database selected[/FONT]
[FONT=arial]dpkg: error processing package mythtv-database (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of mythtv:[/FONT]
[FONT=arial] mythtv depends on mythtv-database; however:[/FONT]
[FONT=arial]  Package mythtv-database is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing package mythtv (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]No apport report written because the error message indicates it's a follow-up error from a previous failure.[/FONT]
[FONT=arial]                                                                                                            Errors were encountered while processing:[/FONT]
[FONT=arial] mythtv-database[/FONT]
[FONT=arial] mythtv[/FONT]
[FONT=arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
[FONT=arial]A package failed to install.  Trying to recover:[/FONT]
[FONT=arial]Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...[/FONT]
[FONT=arial]ERROR 1046 (3D000) at line 22: No database selected[/FONT]
[FONT=arial]dpkg: error processing package mythtv-database (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of mythtv:[/FONT]
[FONT=arial] mythtv depends on mythtv-database; however:[/FONT]
[FONT=arial]  Package mythtv-database is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing package mythtv (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]Errors were encountered while processing:[/FONT]
[FONT=arial] mythtv-database[/FONT]
[FONT=arial] mythtv[/FONT]

---

### Post by tgm4883 on 2014-07-23
> **phillip9 said:**
> hi got the following after upgrading any one know what might be wrong at all any help would be greatly appreciated thanks

[FONT=arial]Couldn't find any package whose name or description matched "full-upgrade"[/FONT]
[FONT=arial]The following partially installed packages will be configured:[/FONT]
[FONT=arial]  mythtv mythtv-database [/FONT]
[FONT=arial]No packages will be installed, upgraded, or removed.[/FONT]
[FONT=arial]0 packages upgraded, 0 newly installed, 0 to remove and 0 not to upgrade.[/FONT]
[FONT=arial]Need to get 0 B of archives. After unpacking 0 B will be used.[/FONT]
[FONT=arial]Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...[/FONT]
[FONT=arial]ERROR 1046 (3D000) at line 22: No database selected[/FONT]
[FONT=arial]dpkg: error processing package mythtv-database (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of mythtv:[/FONT]
[FONT=arial] mythtv depends on mythtv-database; however:[/FONT]
[FONT=arial]  Package mythtv-database is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing package mythtv (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]No apport report written because the error message indicates it's a follow-up error from a previous failure.[/FONT]
[FONT=arial]                                                                                                            Errors were encountered while processing:[/FONT]
[FONT=arial] mythtv-database[/FONT]
[FONT=arial] mythtv[/FONT]
[FONT=arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
[FONT=arial]A package failed to install.  Trying to recover:[/FONT]
[FONT=arial]Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...[/FONT]
[FONT=arial]ERROR 1046 (3D000) at line 22: No database selected[/FONT]
[FONT=arial]dpkg: error processing package mythtv-database (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of mythtv:[/FONT]
[FONT=arial] mythtv depends on mythtv-database; however:[/FONT]
[FONT=arial]  Package mythtv-database is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing package mythtv (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]Errors were encountered while processing:[/FONT]
[FONT=arial] mythtv-database[/FONT]
[FONT=arial] mythtv[/FONT]

You have incorrect data in /etc/mythtv/config.xml

---

