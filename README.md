## Exploring Common Crawl Data with Spark & AWS

Richard Haussman, Chris Stafford, Tyson Ward

*Using Spark and AWS to uncover basic statistics from Common Crawl.*

#### Goals

* Practice Spark
* Practice AWS, including AMAZON EMR, S3, and boto3
* Work with a sub-sample of big data locally first BEFORE training on the full dataset (or a larger subset of the data) on S3.
* Practice scoping a potentially extremely time-intensive project so that you have reliable results in just one day.

#### About Common Crawl

The Common Crawl is a non-profit organization that uses web crawlers to index the world wide web. Besides providing useful search results, data obtained from web crawling has been used to "improve language translation software, predict trends, track disease propagation and more."

#### The Data

* Files types : .warc, .wet, .wat . . .what?: Data are stored in .warc files, which are a combination of .wet and .wat files.  .wat files contained meta data about each website, and .wet files contain the *extracted text* from each webpage.

#### Question

What servers served the most pages?
What words are most common?


|             |                 Spark                |                           Hadoop                          |
|:-----------:|:------------------------------------:|:---------------------------------------------------------:|
|  Filesystem |                  Any                 |                         HDFS only                         |
|    Speed    | Much faster, but uses lots of memory | writes things to local after each step, slows things down |
| Reliability |   Getting better, but a little bug   |                 Very reliable because OLD                 |


Locally, were extracted counts of pages served by several servers using the server_count.py script.

|   Server    |   Pages Served       |
|:-----------:|:------------------------------------:|
|'Apache' | 9084 |
'nginx' | 7543
'cloudflare-nginx' | 3538
'(no server in HTTP header)' | 3490
'GSE' | 2562
'Microsoft-IIS/7.5' | 1802
'Microsoft-IIS/8.5' | 1412
'nginx/1.10.2' | 651
'nginx/1.10.3' | 646
'Apache/2.2.15 (CentOS)' | 620


#### References
* [Common Crawl](http://commoncrawl.org/)
* [*Analyzing Petabytes of Websites*](http://tech.marksblogg.com/petabytes-of-website-data-spark-emr.html) - Mark Litwintschik 
