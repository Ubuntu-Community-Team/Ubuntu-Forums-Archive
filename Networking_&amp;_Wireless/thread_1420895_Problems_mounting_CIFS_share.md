---
title: "Problems mounting CIFS share"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by texastwister on 2010-03-03
A fileshare I have been accessing via mount.cifs for some time has been replaced with a new NAS device. The new share will not mount correctly under Ubuntu, although it does under RHEL 5 and under Windows Vista. It IS accessible via smbclient under Ubuntu (pointing to a problem with the CIFS kernel module?).

**Details**
_Problematic Ubuntu Client_
OS:	Ubuntu 9.10
kernel:	2.6.31-19-generic
smbfs package:	2:3.4.0-3ubuntu5.4
smbclient package: 	2:3.4.0-3ubuntu5.4
cifs.ko:	1.60

_Working RedHat Client_
OS:	Red Hat Enterprise Linux 5.4
kernel:	2.6.18-164-11.1.el5xen
samba-client package:  	3.0.33-3.15.el15_4.1
cifs.ko:	1.57RH

**Expected Behavior**

The following command should mount the share:
```

[root@RH5-3G4DKB1-SLP ~]# mount -t cifs --verbose -o credentials=/etc/.cred.txt,uid=scott,gid=scott,rw //pc1n7i01d03.us.dell.com/DTTUATNAS2/training /tmp/mnttest/

mount.cifs kernel mount options: unc=//pc1n7i01d03.us.dell.com\DTTUATNAS2,ip=10.30.25.221,user=scott_purcell,ver=1,rw,credentials=/etc/.cred.txt,uid=500,gid=500,prefixpath=training,pass=********

```

The share should appear in the list of mounted filesystems:

```
[root@RH5-3G4DKB1-SLP ~]# mount |tail -n 1
//pc1n7i01d03.us.dell.com/DTTUATNAS2/training on /tmp/mnttest type cifs (rw,mand)
```

The files and directories should be visible and accessible as permissions allow:

```
[root@RH5-3G4DKB1-SLP ~]# ls /tmp/mnttest/
6300.jpg                  DVD2_index.asp                HTML.htm          job_aids.asp             reusing.log                        test.htm
about.asp                 e-learning                    HTML_Training     jorge.asp                review                             test_reuse.asp
about_us.asp              Enterprise                    images            legal.asp                rptapppool.xml                     testswf.htm
ABU                       enterprise.htm                Include           legal_process.asp        search.asp                         Thumbs.db
accessibility.asp         enterprise_services_offering  Includes          maintenance.htm          sendmail.asp                       TOOLS
ajaxStatus.htm            FAQ.asp                       index_2.asp       migration.asp            sendmail.asp.txt                   Training
Client                    find.asp                      index.asp         navigation_hoffer.inc    serverid.asp                       training.asp
client_services_offering  find_periods.asp              index_flash.asp   navigation.inc           Servers.asp                        training_header.swf
Consumer                  Flash_Beta                    index_hoffer.asp  navigation.xml           service_level_agreement.asp        Training_in_every_language.swf
dftapppool.xml            folders.txt                   index_new.asp     New_navigation.inc       service_level_agreement_daren.asp  training_old.asp
docinfo.xml               Functions                     index_new_v2.asp  owners.asp               SMB                                trapppool.xml
document_history.xml      GCSS                          index_new_v3.asp  owners_daren.asp         SMB_Ownership                      tree.txt
DSP_CHS                   GLND_Workaids                 index_new_v4.asp  pnp                      space.asp                          triis.xml
DTT                       global.asa                    index_new_v5.asp  profesional_skills.asp   TAM                                unauthorize.asp
dttapppool.xml            Global_NH_Standard            ISO               replication_process.asp  Template                           unauthorize.htm
DVD1_index.asp            Hosted                        Job_Aids          replication_time.asp     test.asp                           User.asp
```

**Actual Behavior**

```
scott@U904-209NVD1-95031:~$ sudo mount -t cifs --verbose -o credentials=/etc/.cred.txt,uid=scott,gid=scott,rw //pc1n7i01d03.us.dell.com/DTTUATNAS2/training /tmp/mnttest/

mount.cifs kernel mount options: unc=//pc1n7i01d03.us.dell.com\DTTUATNAS2,user=scott_purcell,ver=1,rw,credentials=/etc/.cred.txt,uid=1000,gid=1000,prefixpath=training,ip=10.30.25.221,pass=********
```
```

scott@U904-209NVD1-95031:~$ mount |tail -n 1
//pc1n7i01d03.us.dell.com/DTTUATNAS2/training on /tmp/mnttest type cifs (rw,mand)
```

```
scott@U904-209NVD1-95031:~$ ls /tmp/mnttest
ls: cannot access /tmp/mnttest/D: No such file or directory
ls: cannot access /tmp/mnttest/?S: No such file or directory
ls: cannot access /tmp/mnttest/P~1: No such file or directory
ls: cannot access /tmp/mnttest/P~2: No such file or directory
ls: cannot access /tmp/mnttest/_~1: No such file or directory
ls: cannot access /tmp/mnttest/I~1: No such file or directory
ls: cannot access /tmp/mnttest/??Ca: No such file or directory
ls: cannot access /tmp/mnttest/W~1: No such file or directory
ls: cannot access /tmp/mnttest/L~1: No such file or directory
ls: cannot access /tmp/mnttest/-Time : No such file or directory
ls: cannot access /tmp/mnttest/?02/27: No such file or directory
ls: cannot access /tmp/mnttest/-1????w: No such file or directory
ls: cannot access /tmp/mnttest/X64AME: No such file or directory
ls: cannot access /tmp/mnttest/: No such file or directory
ls: cannot access /tmp/mnttest/W~1: No such file or directory
ls: cannot access /tmp/mnttest/?: No such file or directory
ls: cannot access /tmp/mnttest/??????T: No such file or directory
ls: cannot access /tmp/mnttest/?: No such file or directory
ls: cannot access /tmp/mnttest/??: No such file or directory
ls: cannot access /tmp/mnttest/?: No such file or directory
ls: cannot access /tmp/mnttest/??: No such file or directory
ls: cannot access /tmp/mnttest/??????: No such file or directory
ls: cannot access /tmp/mnttest/S~1.ASPaccessibil: No such file or directory
ls: cannot access /tmp/mnttest/T~1.HTMajaxSta: No such file or directory
ls: cannot access /tmp/mnttest/P~1.XMLdftappp: No such file or directory
ls: cannot access /tmp/mnttest/i: No such file or directory
ls: cannot access /tmp/mnttest/E~1.XMLdocument_hist: No such file or directory
ls: cannot access /tmp/mnttest/P~1.XMLdttappp: No such file or directory
ls: cannot access /tmp/mnttest/I~1.ASPDVD1_in: No such file or directory
ls: cannot access /tmp/mnttest/I~1.ASPDVD2_in: No such file or directory
ls: cannot access /tmp/mnttest/P~1.HTMenterpr: No such file or directory
ls: cannot access /tmp/mnttest/Rjeremif: No such file or directory
ls: cannot access /tmp/mnttest/P~1.ASPfind_peri: No such file or directory
ls: cannot access /tmp/mnttest/i_voss.fold: No such file or directory
ls: cannot access /tmp/mnttest/na_mariglo: No such file or directory
ls: cannot access /tmp/mnttest/1.ATRsiH: No such file or directory
ls: cannot access /tmp/mnttest/??J: No such file or directory
ls: cannot access /tmp/mnttest/_~1.ASPindex_fl: No such file or directory
ls: cannot access /tmp/mnttest/_~2.ASPindex_hof: No such file or directory
ls: cannot access /tmp/mnttest/_~3.ASPindex_: No such file or directory
ls: cannot access /tmp/mnttest/_~4.ASPindex_new: No such file or directory
ls: cannot access /tmp/mnttest/56C.ASPindex_new: No such file or directory
ls: cannot access /tmp/mnttest/DE4.ASPindex_new: No such file or directory
ls: cannot access /tmp/mnttest/F5C.ASPindex_new: No such file or directory
ls: cannot access /tmp/mnttest/URI~1.Ajob_a: No such file or directory
ls: cannot access /tmp/mnttest/: No such file or directory
ls: cannot access /tmp/mnttest/_~1.ASPlegal_proc: No such file or directory
ls: cannot access /tmp/mnttest/E~1.HTMmaintena: No such file or directory
ls: cannot access /tmp/mnttest/T~1.ASPmigrat: No such file or directory
ls: cannot access /tmp/mnttest/A~1.INCnavigat: No such file or directory
ls: cannot access /tmp/mnttest/A~1.XMLnavigat: No such file or directory
ls: cannot access /tmp/mnttest/A~2.INCnavigation_hof: No such file or directory
ls: cannot access /tmp/mnttest/A~1.INCNew_navigat: No such file or directory
ls: cannot access /tmp/mnttest/o+refreown: No such file or directory
ls: cannot access /tmp/mnttest/S~1.ASPowners_da: No such file or directory
ls: cannot access /tmp/mnttest/S~1.ASPprofesional_ski: No such file or directory
ls: cannot access /tmp/mnttest/C~1.ASPreplication_proc: No such file or directory
ls: cannot access /tmp/mnttest/C~2.ASPreplication_t: No such file or directory
ls: cannot access /tmp/mnttest/??????Mreus: No such file or directory
ls: cannot access /tmp/mnttest/P~1.XMLrptappp: No such file or directory
ls: cannot access /tmp/mnttest/?: No such file or directory
ls: cannot access /tmp/mnttest/A~1.TXTsendmail.: No such file or directory
ls: cannot access /tmp/mnttest/???????serve: No such file or directory
ls: cannot access /tmp/mnttest/???????Serv: No such file or directory
ls: cannot access /tmp/mnttest/C~1.ASPservice_level_agreem: No such file or directory
ls: cannot access /tmp/mnttest/C~2.ASPservice_level_agreement_da: No such file or directory
ls: cannot access /tmp/mnttest/??J: No such file or directory
ls: cannot access /tmp/mnttest/???????t: No such file or directory
ls: cannot access /tmp/mnttest/R~1.ASPtest_re: No such file or directory
ls: cannot access /tmp/mnttest/ard_kintest: No such file or directory
ls: cannot access /tmp/mnttest/tenanceTh: No such file or directory
ls: cannot access /tmp/mnttest/1.ATRcatrain: No such file or directory
ls: cannot access /tmp/mnttest/I~1.SWFtraining_hea: No such file or directory
ls: cannot access /tmp/mnttest/I~2.SWFTraining_in_every_langu: No such file or directory
ls: cannot access /tmp/mnttest/I~1.ASPtraining_: No such file or directory
ls: cannot access /tmp/mnttest/P~1.XMLtrappp: No such file or directory
ls: cannot access /tmp/mnttest/: No such file or directory
ls: cannot access /tmp/mnttest/SECURIU: No such file or directory
ls: cannot access /tmp/mnttest/H~1.ASPunauthor: No such file or directory
ls: cannot access /tmp/mnttest/H~1.HTMunauthor: No such file or directory
ls: cannot access /tmp/mnttest/???: No such file or directory
ls: cannot access /tmp/mnttest/??????: No such file or directory
ls: cannot access /tmp/mnttest/T~1: No such file or directory
ls: cannot access /tmp/mnttest/??????: No such file or directory
ls: cannot access /tmp/mnttest/???????: No such file or directory
ls: cannot access /tmp/mnttest/?: No such file or directory
ls: cannot access /tmp/mnttest/R~1: No such file or directory
ls: cannot access /tmp/mnttest/T~1: No such file or directory
??                     C~1.ASPreplication_proc            ??J                S~1.ASPprofesional_ski
?                      C~1.ASPservice_level_agreem        ??J                ?SECURIU
?                      C~2.ASPreplication_t               L~1                ???????Serv
?02/27                 C~2.ASPservice_level_agreement_da  ??????Mreus        ???????serve
_~1                    ??Ca                               na_mariglo         ???????t
_~1.ASPindex_fl        D                                  o+refreown         ???????T
_~1.ASPlegal_proc      DE4.ASPindex_new                   P~1                T~1
1.ATRcatrain           E~1.HTMmaintena                    P~1.ASPfind_peri   T~1
?        1.ATRsiH               E~1.XMLdocument_hist               P~1.HTMenterpr     T~1.ASPmigrat
?        -1????w                F5C.ASPindex_new                   P~1.XMLdftappp     T~1.HTMajaxSta
???      _~2.ASPindex_hof       H~1.ASPunauthor                    P~1.XMLdttappp     tenanceTh
??????   _~3.ASPindex_          H~1.HTMunauthor                    P~1.XMLrptappp     -Time
??????   _~4.ASPindex_new       i                                  P~1.XMLtrappp      URI~1.Ajob_a
???????  56C.ASPindex_new       I~1                                P~2                W~1
???????  A~1.INCnavigat         I~1.ASPDVD1_in                     R~1                W~1
????     A~1.INCNew_navigat     I~1.ASPDVD2_in                     R~1.ASPtest_re     X64AME
????     A~1.TXTsendmail.       I~1.ASPtraining_                   Rjeremif
??       A~1.XMLnavigat         I~1.SWFtraining_hea                ?S
??       A~2.INCnavigation_hof  I~2.SWFTraining_in_every_langu     S~1.ASPaccessibil
??       ard_kintest            i_voss.fold                        S~1.ASPowners_da
scott@U904-209NVD1-95031:~$
```

So, does this look like a bug?  Or is there some option that is required in Ubuntu that is set by default in RHEL?

Thank you in advance for any assistance you can give.

Scott

---

### Post by suseendran.rengabashyam on 2010-03-04
Hi,

Try adding 'noserverino' to your mount options i.e
```
sudo mount -t cifs --verbose -o credentials=/etc/.cred.txt,uid=scott,gid=scott,rw,noserverino //pc1n7i01d03.us.dell.com/DTTUATNAS2/training /tmp/mnttest/
```

Source:
[http://old.nabble.com/%22mount--t-cifs%22-garbled-text-after-9.10-upgrade-td26235277.html](http://old.nabble.com/%22mount--t-cifs%22-garbled-text-after-9.10-upgrade-td26235277.html)

[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/406466](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/406466)

Hope this helps.

---

### Post by texastwister on 2010-03-04
Thank you! That resolved it.

---

