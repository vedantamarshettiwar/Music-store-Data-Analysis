# Music-store-Data-Analysis
SELECT c.FirstName, c.LastName, SUM(i.Total) AS TotalSpent
FROM Customers c
JOIN Invoices i ON c.CustomerID = i.CustomerID
GROUP BY c.CustomerID
ORDER BY TotalSpent DESC
LIMIT 5;
SELECT 
    c.Country,
    g.Name AS Genre,
    COUNT(*) AS PurchaseCount
FROM Customers c
JOIN Invoices i ON c.CustomerID = i.CustomerID
JOIN InvoiceLines il ON i.InvoiceID = il.InvoiceID
JOIN Tracks t ON il.TrackID = t.TrackID
JOIN Genres g ON t.GenreID = g.GenreID
GROUP BY c.Country, g.Name
ORDER BY c.Country, PurchaseCount DESC;
SELECT i.BillingCity, SUM(i.Total) AS TotalRevenue
FROM Invoices i
GROUP BY i.BillingCity
ORDER BY TotalRevenue DESC
LIMIT 1;
SELECT e.FirstName, e.LastName, COUNT(c.CustomerID) AS CustomerCount
FROM Employees e
JOIN Customers c ON e.EmployeeID = c.SupportRepID
GROUP BY e.EmployeeID
ORDER BY CustomerCount DESC
LIMIT 1;
SELECT ar.Name AS Artist, SUM(il.Quantity) AS TotalSold
FROM InvoiceLines il
JOIN Tracks t ON il.TrackID = t.TrackID
JOIN Albums al ON t.AlbumID = al.AlbumID
JOIN Artists ar ON al.ArtistID = ar.ArtistID
GROUP BY ar.ArtistID
ORDER BY TotalSold DESC
LIMIT 5;
