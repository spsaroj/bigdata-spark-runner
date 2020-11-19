# Big Data Apache Beam Spark Runner

The main objective of this project is to make a Apache Beam pipeline and run it in Spark.

## Commands:

**Fetching data**

I thought it would be interesting to see the repeating words in the script of my favorite movie, The Godfather I.
To fetch the data into the text file open powershell in the folder where you want to store the text file and run:

 ```curl "https://www.dailyscript.com/scripts/Godfather,%20The.txt" -o "godfatherI.txt"```


**Cleaning the data**

Since we can ignore all the most repeating trivial words like I, am, you, the, a, an, etc. we run the following command in the powershell:

 ```sed -e 's/I / /g;s/ am / /g;s/ you / /g;s/The / /g;s/ the / /g;s/ an / /g;s/ a / /g;s/ in / /g;s/ at / /g;s/ on / /g; s/ is / /g;s/ are / /g; s/Is / /g; s/Are / /g' godfatherI.txt > godfatherI_cleaned.txt```

This will now take all the inputs from godfatherI.txt, cleans it and stores the result in godfatherI_cleaned.txt file.

**Running beam wordcount**

If you are not already in the folder where there is code for wordcount and the godfatherI_cleaned.txt file, run the following in the powershell:

```cd "your directory"```

The following code will take godfatherI_cleaned.txt as an input and will pass it to the output called outputwordCount:

```python -m wordcount --input godfatherI_cleaned.txt --output outputWordCount```

After you run the above command you will see a new file appearing in your directory which will have the list of word counts.


**Running beam wordcount in spark runner**

I couldn't run this code perfectly. My main motif was to run the wordcount.py in the spark. Theoritically the way to do so is to first run spark and then assign a wordcount.py job to it. But I couldn't do it.

```python -m wordcount --input godfatherI_cleaned.txt --output output --runner SparkRunner```



## Visualization
![Graph](https://raw.githubusercontent.com/spsaroj/bigdata-spark-runner/main/chart.PNG)

It is pretty amazing to see how Michael, Don's son in the movie is repeated the most than Don.


## Contributions

All the contributions are more than welcome. If anyone knows how to run the wordcount file in spark don't hesitate to contribute.

## Resources
[https://beam.apache.org/get-started/wordcount-example/](https://beam.apache.org/get-started/wordcount-example/)
[https://github.com/apache/beam/blob/master/sdks/python/apache_beam/examples/wordcount.py](https://github.com/apache/beam/blob/master/sdks/python/apache_beam/examples/wordcount.py)

