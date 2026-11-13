# Web Server Log Analytics & Monitoring System

A Python portfolio project that parses AWS Application Load Balancer (ALB) access logs and turns them into traffic summaries, HTTP status reports, performance statistics, anomaly review flags, and charts.

This project is part of my Python learning journey while I study Generative AI at **Techpanda**. It demonstrates how I apply Python fundamentals and data analysis tools to a practical dataset.

## What the project does

- Parses quoted ALB log entries with Python's `shlex` module.
- Converts each valid entry into named fields and records malformed lines separately.
- Analyzes request counts, client IPs, paths, and traffic over time.
- Reports load balancer and target status codes separately.
- Uses NumPy to calculate timing and response-size statistics.
- Uses Pandas to clean, filter, group, and export records.
- Creates eight Matplotlib charts from the input data.
- Flags potential high-volume minutes, slow target responses, and 5xx responses with simple, explainable rules.

Anomaly flags are intended for review. They do not confirm attacks or security incidents.

## Skills demonstrated

The notebook uses Core Python concepts including variables, lists, dictionaries, loops, functions, file handling, CSV processing, exception handling, and `pathlib`. It also demonstrates parsing quoted text, handling missing values, organizing analysis into steps, and validating results with assertions.

These skills connect with the topics I am studying at Techpanda. My local study materials include Python fundamentals, functions, collections, file handling, exception handling, modules, classes, DSA, NumPy, Pandas, Matplotlib, and introductory machine learning.

## Technology

- Python 3.10 or later
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib

## Run the notebook

1. Install Python and Jupyter.
2. Install the notebook libraries:

   ```bash
   python -m pip install jupyter numpy pandas matplotlib
   ```

3. Place your ALB log in the project folder as `mylog.log`.
4. Open the notebook:

   ```bash
   jupyter notebook Web_Server_Log_Analytics.ipynb
   ```

5. Run the notebook cells from top to bottom.

The first code cell defaults to `C:\projects\Python Project`. On another computer, set the `ALB_PROJECT_DIR` environment variable to the project folder, or edit `PROJECT_DIR` in that cell. The notebook creates its processed-data and report folders automatically.

## Outputs

The notebook writes the parsed dataset to `data/processed/cleaned_logs.csv`, CSV reports to `reports/csv/`, charts to `reports/charts/`, and a JSON run summary. The charts include status-code distribution, requests over time, top clients, request processing time, processing-time comparison, requests by hour, 2xx versus non-2xx responses, and response sizes.

The supplied sample contains 344 parsed records and 7 unique client IP addresses. Its load balancer status counts are 200: 115, 304: 186, and 404: 43. A 304 is reported as “Not Modified,” separately from actual redirection responses. Your counts will depend on the input log.

## Dataset privacy

ALB logs can contain internal IP addresses, hostnames, AWS resource identifiers, trace IDs, and private request details. **Do not commit the original `mylog.log` or unsanitized reports to GitHub.** Before publishing, create a sanitized sample, review every output, and add the raw log and generated reports to `.gitignore`.

## Scope and limitations

The parser is designed for the AWS ALB log structure used by this project. Apache, Nginx, NASA, and other server logs use different formats and need their own parser or adapter. The anomaly thresholds are descriptive and based on the current dataset; they are not universal service thresholds. The notebook loads this small sample into memory and would need batch processing for very large logs.

## Next improvements

- Add a second parser for Apache or Nginx logs.
- Add automated unit tests and a command-line entry point.
- Prepare a sanitized sample dataset and public screenshots.
- Compare percentile-based flags with operational thresholds.

## Learning goal

This project is intended to help me explain how I use Python to read and validate data, structure records, analyze patterns, calculate statistics, and communicate results with visualizations as I continue my Generative AI studies at Techpanda.
"# Web-Server-Log-Analytics-Monitoring-System" 
