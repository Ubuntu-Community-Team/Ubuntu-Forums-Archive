---
title: "Cannot print to windows server"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by Artemus on 2010-06-16
I'm running Lucid 64 bit. I've added a printer that is on a windows server using system-config-printer. I was able to browse to the printer using smb://dept-prntsrv/ and entering the username and password when it was requested. However, when I try to print a test page it fails and displays the following in the Printer Properties window:

Printer State: Idle - NT_STATUS_ACCESS_DENIED opening remote spool Test Page

I know the share is valid as I can use it from a virtual windows box running in VirtualBox on this Ubuntu machine, and smbclient gives the following:

     $ smbclient -L dept-prntsrv -Uusername%password

     Domain=[UNIV] OS=[Windows Server (R) 2008 Standard 6002 Service Pack 2] Server=[Windows Server (R) 2008 Standard 6.0]
     Domain=[UNIV] OS=[Windows Server (R) 2008 Standard 6002 Service Pack 2] Server=[Windows Server (R) 2008 Standard 6.0]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Drivers         Disk
        DEPT-301-Laser2200 Printer   301 HP LaserJet 2200
        DEPT-RM101-TSLPrinter Printer   TSL Printer
        DEPT-RM103-LaserJet2430 Printer   DLD Lab
        DEPT-RM202-ColorLaser Printer   Color LaserJet
        DEPT-RM202-Kyocera Printer   Copier
        DEPT-RM202-LargeFormat Printer   Large Format Printer
        DEPT-RM202-Laser2300 Printer   Black and White Laser
        DEPT-RM303-Laser2100 Printer   Black and White Laser
        DEPT-RM401-Laser2430 Printer   401 HP LaserJet 2430
        DEPT-RM411-Laser Printer   411 HP LaserJet 2430
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        prnproc$        Disk      Printer Drivers

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------




The entry in /etc/cups/printers.conf that was added by system-config-printer:

     <Printer Kyocera-Mita-KM-5035>
     AuthInfoRequired username,password
     Info Kyocera Mita KM-5035
     MakeModel Kyocera Mita KM-5035
     DeviceURI smb://username:password@dept-prntsrv/DEPT-RM202-Kyocera
     State Idle
     StateTime 1276706367
     Type 8400980
     Filter application/vnd.cups-raw 0 -
     Filter application/vnd.cups-command 0 commandtops
     Filter application/vnd.cups-postscript 0 -
     Accepting Yes
     Shared Yes
     JobSheets none none
     QuotaPeriod 0
     PageLimit 0
     KLimit 0
     OpPolicy default
     ErrorPolicy retry-job
     </Printer>


Any suggestions?

---

### Post by Artemus on 2010-06-17
I should add that the test job submitted has a status "Held for authentication" and a window titled "Authentication" with the text "Authentication required for printing document `Test Page' (job 411)" asking for a username and password keeps re-appearing no matter what username and password I give.

---

### Post by trukker on 2012-06-17
I have the same problem on upgrading to 12.04

---

### Post by mErchamion on 2012-06-25
Same issue here, server and client are ubuntu 12.04 sharing via samba,

---

